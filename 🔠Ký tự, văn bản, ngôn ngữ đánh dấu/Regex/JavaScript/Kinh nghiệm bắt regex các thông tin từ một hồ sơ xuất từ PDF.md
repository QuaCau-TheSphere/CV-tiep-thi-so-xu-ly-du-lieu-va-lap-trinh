---
share: true
created: 2023-10-30T14:29
updated: 2024-11-21T12:27
---
```ts
/**
 * Tạo một mảng ngoài để có thể bắt kiểu tốt hơn. Xem chi tiết: https://github.com/microsoft/TypeScript/issues/36029#issuecomment-571810506
 */
const init = [
  ["Tên KH", /(?<=Tên\sKH:\s).*(?=\sCMND)/s],
  ["Giới tính", /(?<=Giới\stính:\s).*(?=\sNăm\ssinh)/],
  ["Ngày sinh", /(?<=Năm\ssinh:\s).*(?=\s)/],
  ["SĐT KH", /(?<=SĐT\sKH:\s)\d*(?=\s)/],
  ["Tạm trú", /(?<=Đ\/c Tạm trú:\s).*/],
  ["Hộ khẩu", /(?<=Đ\/c Hộ khẩu:\s).*/],
  ["Làm việc", /(?<=Đ\/c Làm việc:\s).*/],

  /** Thông tin khoản vay */
  ["Số HĐ", /(?<=Số\sHĐ:\s).*?(?=\s)/],
  ["Sản phẩm", /(?<=Sản phẩm:\s).*?(?=\s)/],
  ["Hạn thanh toán", /(?<=Hạn\sthanh\stoán:\s).*?(?=\s)/],
  ["Ngày TT", /(?<=Ngày TT:\s).*?(?=\s)/],
  ["Trạng thái", /(?<=Trạng thái:\s).*?(?=\s)/],

  /** Thông tin quá hạn */
  ["Số ngày quá hạn", /(?<=Số\sngày\squá\shạn:\s).*?(?=\s)/],
  ["Thanh toán gần nhất", /(?<=Thanh\stoán\sgần\snhất:\s).*/],
  ["Lịch sử TT gần nhất", /(?<=Lịch\ssử\sTT\sgần\snhất:\s).*/],
  ["Hạn mức thẻ hiện tại", /(?<=Hạn\smức\sthẻ\shiện\stại\s).*(?=\s)/],
  ["Hạn mức thẻ cũ", /(?<=Hạn\smức\sthẻ\scũ\s).*(?=\s)/],
  ["Khoản vay", /(?<=Khoản vay:\s).*(?=\sNgày ký)/],
  ["POS FULL", /(?<=POS FULL:\s).*(?=\stất\stoán\shợp\sđồng)/],
  ["Tiền lãi", /(?<=Tiền\slãi:\s).*(?=\s)/],
  ["Lãi quá hạn", /(?<=Lãi\squá\shạn:\s).*(?=\s)/],
  ["Tổng dư nợ phải thanh toán", /(?<=Tổng\sdư\snợ\sphải\sthanh\stoán:\s).*(?=\s)/],
] as const;

type TênTrường = typeof init[number][0];
const danhMụcRegex: Map<TênTrường, RegExp> = new Map(init);

const dsLỗi = [
  "❌ Hồ sơ gốc ghi cụ thể là NULL",
  "❌ Regex không tìm được kết quả",
  "❌ Hồ sơ gốc không có trường này",
  "❌ Hồ sơ không ghi dữ liệu",
] as const;
export type Lỗi = typeof dsLỗi[number];

export function làLỗi(biến: string | number | Temporal.PlainDate | ThanhToánGầnNhất | ĐịaChỉ | Lỗi): biến is Lỗi {
  if (dsLỗi.includes(biến as Lỗi)) return true;
  return false;
}

export function lấyRaw(trường: string, hồSơ: string): string | Lỗi {
  // const regexTrường = new RegExp(trường.replaceAll(" ", "\\s"));
  // if (!regexTrường.test(hồSơ)) return {lỗi: "Hồ sơ gốc không có trường này"}

  const raw = (danhMụcRegex.get(trường) as RegExp).exec(hồSơ);
  if (!raw) return dsLỗi[1];
  if (raw[0].includes("NULL")) return dsLỗi[0];

  return raw[0];
}

export function lọcTênKH(hồSơ: string) {
  const raw = lấyRaw("Tên KH", hồSơ);
  if (typeof raw !== "string") return raw;
  return raw.replaceAll("\n", " ");
}

function lọcGiớiTính(hồSơ: string) {
  const raw = lấyRaw("Giới tính", hồSơ);
  if (typeof raw !== "string") return raw;
  if (raw === "FEMALE") return "nữ";
  return "nam";
}

function lọcNgàySinh(hồSơ: string) {
  const raw = lấyRaw("Ngày sinh", hồSơ);
  if (typeof raw !== "string") return raw;
  const [ngày, tháng, năm] = raw.split("/");
  return new Temporal.PlainDate(parseInt(năm), parseInt(tháng), parseInt(ngày));
}

function lọcSĐT(hồSơ: string) {
  const raw = lấyRaw("SĐT KH", hồSơ);
  if (typeof raw !== "string") return raw;
  return raw.slice(0, 2) === "84" ? raw.replace("84", "0") : raw;
}

/** Thông tin khoản vay */
function lọcSốHĐ(hồSơ: string) {
  return lấyRaw("Số HĐ", hồSơ);
}

function lọcSảnPhẩm(hồSơ: string) {
  return lấyRaw("Sản phẩm", hồSơ);
}

function lọcKhoảnVay(hồSơ: string) {
  const raw = lấyRaw("Khoản vay", hồSơ);
  if (typeof raw !== "string") return raw;
  return parseInt(raw.replaceAll(".", ""));
}

function lọcHạnThanhToán(hồSơ: string) {
  const raw = lấyRaw("Hạn thanh toán", hồSơ);
  if (làLỗi(raw)) return raw;
  const [ngày, tháng, năm] = raw.split("/");
  return new Temporal.PlainDate(parseInt(năm), parseInt(tháng), parseInt(ngày));
}

function lọcNgàyThanhToán(hồSơ: string) {
  const raw = lấyRaw("Ngày TT", hồSơ);
  if (làLỗi(raw)) return raw;
  const [ngày, tháng, năm] = raw.split("/");
  return new Temporal.PlainDate(parseInt(năm), parseInt(tháng), parseInt(ngày));
}

function lọcHạnMứcThẻCũ(hồSơ: string) {
  const raw = lấyRaw("Hạn mức thẻ cũ", hồSơ);
  if (typeof raw !== "string") return raw;
  return parseInt(raw.replaceAll(".", ""));
}

function lọcHạnMứcThẻHiệnTại(hồSơ: string) {
  const raw = lấyRaw("Hạn mức thẻ hiện tại", hồSơ);
  if (typeof raw !== "string") return raw;
  return parseInt(raw.replaceAll(".", ""));
}

function lọcTrạngThái(hồSơ: string) {
  return lấyRaw("Trạng thái", hồSơ);
}

/** Thông tin quá hạn */
function lọcSốNgàyQuáHạn(hồSơ: string) {
  const raw = lấyRaw("Số ngày quá hạn", hồSơ);
  if (typeof raw !== "string") return raw;
  return parseInt(raw);
}

function lọcTTGầnNhất(hồSơ: string): ThanhToánGầnNhất | Lỗi {
  let raw = lấyRaw("Thanh toán gần nhất", hồSơ);
  if (làLỗi(raw)) {
    const temp = lấyRaw("Lịch sử TT gần nhất", hồSơ);
    if (làLỗi(temp)) return raw;
    raw = temp;
  }
  if (!/\|\s/.test(raw as string)) return { sốTiền: 0, thờiĐiểm: null };
  const splittedRaw = (raw as string).split(/(?<=\d)\s(?=20)/);
  const [rawThờiĐiểm, rawSốTiền] = splittedRaw[0].split(/\|\s/);
  const rawThờiĐiểmSplited = rawThờiĐiểm.split("/");

  let ngày = 1, tháng = 1, năm = 2024;
  if (rawThờiĐiểmSplited.length === 2) {
    tháng = parseInt(rawThờiĐiểmSplited[1]);
    năm = parseInt(rawThờiĐiểmSplited[0]);
  } else if (rawThờiĐiểmSplited.length === 3) {
    ngày = parseInt(rawThờiĐiểmSplited[0]);
    tháng = parseInt(rawThờiĐiểmSplited[1]);
    năm = parseInt(rawThờiĐiểmSplited[2]);
  }

  return {
    sốTiền: parseInt(rawSốTiền.replaceAll(",", "")),
    thờiĐiểm: new Temporal.PlainDate(năm, tháng, ngày),
  };
}

function lọcPosFull(hồSơ: string) {
  const raw = lấyRaw("POS FULL", hồSơ);
  if (typeof raw !== "string") return raw;
  return parseInt(raw.replaceAll(".", ""));
}

function lọcTổngDưNợ(hồSơ: string) {
  const raw = lấyRaw("Tổng dư nợ phải thanh toán", hồSơ);
  if (typeof raw !== "string") return raw;
  return parseInt(raw.replaceAll(".", ""));
}

function lọcTiềnLãi(hồSơ: string) {
  const rawTiềnLãi = lấyRaw("Tiền lãi", hồSơ);
  if (!làLỗi(rawTiềnLãi)) {
    return parseInt((rawTiềnLãi as string).replaceAll(".", ""));
  } else {
    const rawLãiQuáHạn = lấyRaw("Lãi quá hạn", hồSơ);
    if (!làLỗi(rawLãiQuáHạn)) return parseInt((rawLãiQuáHạn as string).replaceAll(".", ""));
    return rawTiềnLãi as Lỗi;
  }
}
export interface ThôngTinTừHồSơ {
  tênKH: string | Lỗi;
  cccdCmnd?: string | Lỗi;
  sđt: string | Lỗi;
  giớiTính: "nam" | "nữ" | Lỗi;
  ngàySinh: Temporal.PlainDate | Lỗi;
  địaChỉTạmTrú: ĐịaChỉ | Lỗi;
  địaChỉThườngTrú: ĐịaChỉ | Lỗi;
  địaChỉLàmViệc: ĐịaChỉ | Lỗi;
  sốHĐ: string | Lỗi;
  sảnPhẩm: string | Lỗi;
  trạngThái: string | Lỗi;
  hạnThanhToán: Temporal.PlainDate | Lỗi;
  ngàyThanhToán: Temporal.PlainDate | Lỗi;
  posFull?: number | Lỗi;
  khoảnVay?: number | Lỗi;
  hạnMứcThẻCũ?: number | Lỗi;
  hạnMứcThẻHiệnTại?: number | Lỗi;
  sốNgàyQuáHạn?: number | Lỗi;
  tiềnLãi?: number | Lỗi;
  thanhToánGầnNhất?: ThanhToánGầnNhất | Lỗi;
  tổngDưNợ: number | Lỗi;
}

export class ThôngTinTừHồSơ {
  constructor(hồSơ: string) {
    return {
      tênKH: lọcTênKH(hồSơ),
      cccdCmnd: undefined,
      sđt: lọcSĐT(hồSơ),
      giớiTính: lọcGiớiTính(hồSơ),
      ngàySinh: lọcNgàySinh(hồSơ),
      địaChỉTạmTrú: lọcĐịaChỉ(hồSơ, "Tạm trú"),
      địaChỉThườngTrú: lọcĐịaChỉ(hồSơ, "Hộ khẩu"),
      địaChỉLàmViệc: lọcĐịaChỉ(hồSơ, "Làm việc"),
      sốHĐ: lọcSốHĐ(hồSơ),
      sảnPhẩm: lọcSảnPhẩm(hồSơ),
      trạngThái: lọcTrạngThái(hồSơ),
      hạnThanhToán: lọcHạnThanhToán(hồSơ),
      ngàyThanhToán: lọcNgàyThanhToán(hồSơ),
      hạnMứcThẻHiệnTại: lọcHạnMứcThẻHiệnTại(hồSơ),
      hạnMứcThẻCũ: lọcHạnMứcThẻCũ(hồSơ),
      posFull: lọcPosFull(hồSơ),
      khoảnVay: lọcKhoảnVay(hồSơ),
      tiềnLãi: lọcTiềnLãi(hồSơ),
      thanhToánGầnNhất: lọcTTGầnNhất(hồSơ),
      sốNgàyQuáHạn: lọcSốNgàyQuáHạn(hồSơ),
      tổngDưNợ: lọcTổngDưNợ(hồSơ),
    };
  }
}

```