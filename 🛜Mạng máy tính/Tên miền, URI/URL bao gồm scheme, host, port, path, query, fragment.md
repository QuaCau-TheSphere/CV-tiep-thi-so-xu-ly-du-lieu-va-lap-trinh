---
share: true
created: 2023-09-27T22:04
updated: 2024-09-26T10:49
---
# How The URL Was Built
![How The URL Was Built](https://cdn-images.welcometothejungle.com/oNKNwujNe-mhEBk94_L0q6kDeK-uwlHvXpQvFqyqQe8/rs:auto:980::/q:85/czM6Ly93dHRqLXByb2R1Y3Rpb24vdXBsb2Fkcy9hcnRpY2xlL2ltYWdlLzAzMjUvMTU5MzY4L1VSTC5wbmc)

author [Sarvesh Mathi](https://www.welcometothejungle.com/en/authors/sarvesh-mathi)

The Internet is one of the greatest inventions of mankind, but it would have amounted to little if not for the World Wide Web (WWW). So much so that we use the two words “Internet” and “Web” synonymously. Technically, the Internet is the [infrastructure](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work) connecting billions of computers together, and the Web is a service built on top of this. The Web is what we use every day to do everything from looking up information to connecting with people across the world.

The Web was invented as a solution to the problem of passing around information between computers. Although this was possible before the Web, the absence of a uniform format and protocol made the whole process cumbersome. _“Often it was just easier to go and ask people when they were having coffee,”_[writes Sir Tim Berners-Lee](https://www.w3.org/People/Berners-Lee/Kids.html#keep), who invented the WWW in 1989. _“I actually wrote some programs to take information from one system and convert it so it could be inserted into another system. More than once. And when you are a programmer, and you solve one problem and then you solve one that’s very similar, you often think, ‘Isn’t there a better way? Can’t we just fix this problem for good?’ That became, ‘Can’t we convert every information system so that it looks like part of some imaginary information system that everyone can read?’ And that became the WWW.”_

The WWW stands on three pillars: [HTML](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics), the language we use to make web pages; [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview), the protocol we use to send and receive resources over the Internet; and the [URL](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL). Here, we’ll explore the history and role of each of the components that make up the URL, which [Berners-Lee describes](https://www.w3.org/DesignIssues/Architecture.html) as the _“most fundamental specification of Web architecture.”_

## What is the URL?

Once we expand the abbreviation, URL becomes self-explanatory. The uniform resource locator is simply an address to a resource on the Internet, most often a web page.

When we wish to access a resource on the Web, the web browser on our computer has to connect to the [web server](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_web_server) hosting the desired resource and locate the resource within this server. The details for which web server to connect to, where to look within the server, and what to look for are specified in the URL.

We mostly use URLs by either directly typing them into the browser’s address bar or by clicking on [hyperlinks](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_hyperlinks).

A URL is made of multiple components, each with its own history and purpose. Here’s a breakdown of these components:

URL Syntax:  
scheme: [ // [ userinfo@ ] host [ :port ] ] [ / ] [ path ] [ ?query ] [#fragment ]

Example:

![image](https://cdn.welcometothejungle.co/uploads/image/file/6023/159368/68dca0f2-7683-4ba9-a87a-3a7fdbe8015e.png)

## Scheme: Which protocol to use?

![image](https://cdn.welcometothejungle.co/uploads/image/file/4115/159368/3effb769-93d1-400c-92b6-dda32a3afffc.png)

The scheme is the first component of the URL. It declares how your web browser should communicate with the web server by specifying the protocol to use. Everything that follows the scheme depends on the type of protocol in use.

You’ve probably only come across the http or https protocols and you might wonder why something so universal must be specified. Historically, this wasn’t the case. Before the Web, the FTP and Gopher protocols were commonly used. The URL syntax was designed to accommodate these old standards as well as be flexible enough for any new standards. Fortunately, HTTP became the popular standard over time. As Berners-Lee writes, inventing the Web was easy—_“The amazing thing which makes it work is that so many people actually have made web servers, and that they all work the same way, on the Internet. They all use HTTP.”_ As a result of this widespread adoption, most browsers autofill URLs with the default http/https protocols, even if you forget to type them out. However, less-common protocols, such as ftp and mailto, are still in use in some cases, and they need to be explicitly specified.

## Host: The most well-known component

![image](https://cdn.welcometothejungle.co/uploads/image/file/4130/159368/01c37f3c-3b77-46d7-ad30-88fa72dea06e.png)

Following the colon, which indicates the end of the scheme, the authority component, which consists of the userinfo and host, begins with a double slash. Why the double slash? Berners-Lee simply copied it from [the Apollo computer](https://www.hpmuseum.net/divisions.php?did=28), a high-end workstation at the time. It was used in Apollo to show a separation between the machine name and path. In the URL, it shows a separation between the scheme and host. But [Berners-Lee confesses](http://news.bbc.co.uk/2/hi/technology/8306631.stm) that the double slash is unnecessary. _“Look at all the paper and trees that could have been saved if people had not had to write or type out those slashes on paper over the years—not to mention the human labor and time spent typing those two keystrokes countless millions of times in browser address boxes,”_[he jokes](https://bits.blogs.nytimes.com/2009/10/12/the-webs-inventor-regrets-one-small-thing/).

Following the double slash is the optional userinfo substring that is absent in our example above. This substring was in the format username:password, but it soon became evident that anyone snooping on the connection could decipher the password. As a result, the password component is no longer in use. The userinfo component is also rarely used nowadays, except with the mailto protocol.

Following the userinfo is the host. The host is the most well-known component of the URL because it consists of the domain name. For example, www.welcometothejungle.com. The web browser uses this name to fetch the IP address of the web server hosting the desired page. Alternatively, we can directly specify the IP address as the host, but you’ll surely agree that it’s much easier to remember welcometothejungle.com than 52.211.16.159, for instance.

The components of the domain name are split by a period (.), but it could have easily been an exclamation mark (!), which was the standard convention used with a popular data transfer tool called UUCP back then. However, the pioneers of the domain name system (DNS) used the period, for no specific reason, and we stuck with that.

The www part of the domain identifies the address as a website. We merely use it because of historical convention. Back then, a single server served multiple purposes, the www indicated that a particular subdomain of the server was for website hosting. This is no longer true because we now have dedicated web servers. As a result, omitting www won’t do any harm. When the site has a subdomain—for example, en. Wikipedia.org—the www is replaced with the subdomain.

After the www comes the actual domain name itself. Since humans prefer working with easy-to-remember names, such as google.com and bbc.co.uk, but web browsers work only with IP addresses, there needs to be a way to translate from one to the other. In the early days of the ARPANET, the US Department of Defense project that was a precursor to the modern Internet, this was done manually by people who kept track of computers and their respective IP addresses and passed on this information if someone requested it. However, with billions of computers around the world, this is clearly impractical now. Manual handling of this information also meant it was not possible to get the IP address of a recently added host after normal working hours or on holidays. _“If you wanted to add a machine to the network, you had to call SRI [Stanford Research Institute], and you would talk to the Network Information Center and ask for a name and an address. The problem is that SRI was off during Christmas week, and they went home on weekdays,”_[says Dr. Paul Mockapetris](https://www.wired.com/2012/07/paul-mockapetris-dns/), inventor of the DNS, which solved these issues for us.

The DNS works like a phone book, matching domain names to their IP address(es). The whole process is strikingly similar to [how telephones used to operate](https://thehistoryoftheweb.com/history-of-the-url/) with the switchboard operators of yesteryear. When you enter a domain name into the address bar of the web browser, here’s what happens:

1. The browser looks through [caches](https://www.lifewire.com/what-is-a-dns-cache-817514). If the cache has the IP address, the DNS query process ends there.
2. If not, the computer connects to a specialized server called [the DNS recursive resolver](https://www.cloudflare.com/learning/dns/what-is-dns/), which in turn, goes around looking for the IP address of the requested domain.
3. The DNS resolver first asks the root name server, which then points to a top-level domain (TLD) name server (such as com or edu), which then points toward servers lower in the hierarchy.
4. Ultimately, the DNS returns the IP address for the requested domain name to the web browser. Since a domain can be mapped to multiple IP addresses, the most relevant one, based on factors such as location of the user or server load, is returned.
5. With the IP address, the web browser is ready to establish a connection with the web server hosting the desired domain. But we need one more component: the port number.

The port number, which is preceded by a colon, indicates which “gate” on the web server to use. If the web server uses standard ports (80 for http and 443 for https), then it is not necessary to specify the port in the URL. If not, then the port must be explicitly declared.

The concept of port numbers predates the Web and even the Internet. Port numbers were used in the ARPANET to send messages to specific applications in a machine. Different port numbers were used for different applications. This idea was carried forward to servers, and subsequently, web servers. It enables the use of the same server for different purposes.

Once [we establish a connection](https://medium.com/@maneesha.wijesinghe1/what-happens-when-you-type-an-url-in-the-browser-and-press-enter-bb0aa2449c1a) by sending an HTTP request to the web server using the IP address and port number, we can then ask for specific pages hosted by that server. We specify the location of these pages in the path component of the URL. If we don’t, we are taken to the default home page of the domain.

## Path: A familiar syntax

![image](https://cdn.welcometothejungle.co/uploads/image/file/4145/159368/153ac226-4550-419c-b938-f073cc022298.png)

The path component begins with a slash and is a sequence of slash-separated segments referring to a specific resource belonging to the domain. The slashes maintain a hierarchical syntax—in other words, the term on the left of a slash is the parent of the term on the right.

If this looks similar to the paths of folders and files in your computer, it’s not by accident. This naming convention was first introduced in [the MULTICS system](https://www.multicians.org), an early time-sharing operating system that used the greater-than symbol (>) to separate items. This was replaced with the slash (/) by Unix programmers. It is now used by both Windows and Mac operating systems. _“The relative URI syntax is just unix pathname syntax reused without apology. Anyone who had used unix would find it quite obvious,”_[writes Berners-Lee](https://www.w3.org/People/Berners-Lee/FAQ.html#InternetWeb).

The path syntax can also consist of dot (.) and double-dots (..) to refer to relative path references. These operate similarly in logic to file directories on our computers. URLs can function with only the path component if they are located in a page for which the browser already has information about the scheme and host. These URLs are known as relative URLs as opposed to the full-form absolute URLs.

## Query: The essential component for dynamic web pages

![image](https://cdn.welcometothejungle.co/uploads/image/file/4161/159368/69fce1ad-6dcc-434f-a711-173d9f38e2d9.png)

On many websites we can interact with a page by providing additional details. These are called dynamic web pages and they allow some kind of input and return information based on that input. The best example of this is when we input a search term in Google and it returns a list of all relevant websites from its database. Our input is specified in the query component of a URL.

The query component begins with a ? and is followed by key/value pairs. Although there is no well-defined syntax, the query component is generally in the format ?key1=value1&key2=value2. The web server uses these key/value parameters to obtain the requested content and then sends it to the web browser. The information passed using the key/value pairs is specific to a website and not universal.

Some websites use a semicolon (;) as the delimiter instead of an ampersand (&), but when the URL was first introduced, queries were separated by [the plus (+) character](https://www.w3.org/History/19921103-hypertext/hypertext/WWW/Addressing/Search.html). This was quickly replaced as people started to abuse this feature by running math operations. [Many other suggestions](https://blog.cloudflare.com/the-history-of-the-url/) were taken into consideration, but ultimately the ampersand proposed by Marc Andreessen, the co-author of the first widely used browser, Mosaic, became the popular choice.

## Fragment: The reason you don’t have to scroll

![image](https://cdn.welcometothejungle.co/uploads/image/file/4184/159368/0bf27547-46be-41ce-8dd8-c4a0c230b492.png)

The final component of a URL is the fragment, and it starts with a hash (#). It is an optional term that is an anchor to a certain part of the page or resource we are accessing. For example, if this paragraph you’re reading has the HTML id=fra, then #fra can be specified in the URL to direct the user to this part of the page without having to scroll down. For a video resource, it can be used to jump users to a specific time.

Since this component does not contain any useful information for the web server, it is never actually sent with the HTTP request. Instead, the web browser handles its function.

The idea of using the hash for this purpose has a strange commonality and history to it. _“It turned out later that, in fact, another hypertext project of some sort in IBM, and Doug Englebart’s NLS system, had both independently used ‘#’ for this purpose. So there is something to choosing a character for the way people think of it,”_ writes Berners-Lee.

To him this idea stemmed from the US address system. _“In a snail mail address in the US at least, it is common to use the number sign for an apartment number or suite number within a building. So 12 Acacia Av #12 means ‘The building at 12 Acacia Av, and then within that the unit numbered 12.’ It seemed to be a natural character for the task. Now, `http://www.example.com/foo#bar` means ‘Within resource `http://www.example.com/foo`, the particular view of it known as bar,’”_ Berners-Lee continues.

The analogy of the postal address ties together all that we’ve read so far. _“URLs are to the Web as addresses are to the world of physical resources we want to find and use,”_ says Keith Shafer, Senior Lecturer, Computer Science & Engineering at Ohio State University, and a pioneer in trying [to fix the problem of broken URLs](https://archive.org/services/purl/help).

Despite its ubiquity, Berners-Lee and [others](https://djangodeployment.com/2017/02/15/history-of-the-url/) think that URL design is not the most optimal. While the host part goes from the more specific (welcometothejungle) to the more general (.com), the path goes from the more general to the more specific. _“I have to say that now I regret that the syntax is so clumsy. I would like `http://www.example.com/foo/bar/baz` to be just written `http:com/example/foo/bar/baz` where the client would figure out that `www.example.com` existed and was the server to contact. But it is too late now,”_ writes Berners-Lee, [adding in 2012](https://www.wired.com/2012/06/sir-tim-berners-lee/): _“The URL will be the last thing to change because that’s the thing that ties it all together.”_

_This article is part of Behind the Code, the media for developers, by developers. Discover more articles and videos by visiting [Behind the Code](https://www.welcometothejungle.com/collections/behind-the-code)!_

Nguồn:: [How The URL Was Built](https://www.welcometothejungle.com/en/articles/btc-url-internet)
[URL as UI](https://www.nngroup.com/articles/url-as-ui/)