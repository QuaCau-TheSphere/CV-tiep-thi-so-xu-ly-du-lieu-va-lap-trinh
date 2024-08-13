---
share: true
created: 2023-10-30T14:29
updated: 2024-08-05T22:32
---
// TypeScript is a Structural Type System. A structural type
// system means that when comparing types, TypeScript only
// takes into account the members on the type.

// This is in contrast to nominal type systems, where you
// could create two types but could not assign them to each
// other. See example:nominal-typing

// For example, these two interfaces are completely
// transferrable in a structural type system:

interface Ball {
  diameter: number;
}
interface Sphere {
  diameter: number;
}

let ball: Ball = { diameter: 10 };
let sphere: Sphere = { diameter: 20 };

sphere = ball;
ball = sphere;

// If we add in a type which structurally contains all of
// the members of Ball and Sphere, then it also can be
// set to be a ball or sphere.

interface Tube {
  diameter: number;
  length: number;
}

let tube: Tube = { diameter: 12, length: 3 };

tube = ball;
ball = tube;

// Because a ball does not have a length, then it cannot be
// assigned to the tube variable. However, all of the members
// of Ball are inside tube, and so it can be assigned.

// TypeScript is comparing each member in the type against
// each other to verify their equality.

// A nominal type system means that each type is unique
// and even if types have the same data you cannot assign
// across types.

// TypeScript's type system is structural, which means
// if the type is shaped like a duck, it's a duck. If a
// goose has all the same attributes as a duck, then it also
// is a duck. You can learn more here: example:structural-typing

// This can have drawbacks, for example there are cases
// where a string or number can have special context and you
// don't want to ever make the values transferrable. For
// example:
//
// -  User Input Strings (unsafe)
// -  Translation Strings
// -  User Identification Numbers
// -  Access Tokens

// We can get most of the value from a nominal type
// system with a little bit of extra code.

// We're going to use an intersectional type, with a unique
// constraint in the form of a property called __brand (this
// is convention) which makes it impossible to assign a
// normal string to a ValidatedInputString.

type ValidatedInputString = string & { __brand: "User Input Post Validation" };

// We will use a function to transform a string to
// a ValidatedInputString - but the point worth noting
// is that we're just _telling_ TypeScript that it's true.

const validateUserInput = (input: string) => {
  const simpleValidatedInput = input.replace(/\</g, "≤");
  return simpleValidatedInput as ValidatedInputString;
};

// Now we can create functions which will only accept
// our new nominal type, and not the general string type.

const printName = (name: ValidatedInputString) => {
  console.log(name);
};

// For example, here's some unsafe input from a user, going
// through the validator and then being allowed to be printed:

const input = "alert('bobby tables')";
const validatedInput = validateUserInput(input);
printName(validatedInput);

// On the other hand, passing the un-validated string to
// printName will raise a compiler error:

printName(input);

// You can read a comprehensive overview of the
// different ways to create nominal types, and their
// trade-offs in this 400 comment long GitHub issue:
//
// https://github.com/Microsoft/TypeScript/issues/202
//
// and this post is a great summary:
//
// https://michalzalecki.com/nominal-typing-in-typescript/

Nguồn:: [TypeScript: TS Playground - An online editor for exploring TypeScript and JavaScript](https://www.typescriptlang.org/play/?#code/PTAEEFQOwewWwJZQIYBtQBcCeAHApqAM5aEZ5yhx7JSGYAWyGo1AxvZrgQnQK5QIAjrzwAoEKBoATFgDc8UUAgBmnfHUbyGBQsiqgpTZKCwxeoVjVjNkhQggDmUcWGSsATjDtq8hAHSiLqAAKlwAyh4IOBgA5HTY+EQkZBQ8RBjuvKwYvO5oADSgAO70COyU1LRBKto+SnSEjPgyqAgA1gTGUllthQixdF09fqAAkqrIQQ4wXgSMg6joGPQ6ep0YGQgARrxkg4MGPYXLCko2qIQw1QfdrG0jAJpmFjSgqNTuinAw7nN4vwAuFgADz0OHeANImWyuTQAFoEkgHIEJMFSnRLIpNAQpHkils3G1CIVlD8QWD3tpfpJqZZCL4giV-p10u4kaAyVBeHAtv8XljkFpCPhWAg0BYYFAyMCbFAZKZeEEpJKYswijRmBgYHI+XBkB1arI0CJ4nlaMp-nktu8RgAxH5BPCguDgvAAlxBOGgUAAVXp7jGUBwu1AYU2UAcdAAFPxdBaAJSe73BM2EVBMBCS0PhyNJ33+sZSBQYFRlDNZgBy3N57kIefArFYvjowRgHSqQQA6gRMaAHHhmN9SBzVCdQEbUCJQMpPBRjLBECgllwgsRSORiv0OMZWhtKVt+iOQRljKwYEWAl28DFqdN2VrQLx6ZJFEgyLW8NlM0ufIUilvJEfARhDECQz1oE83yURQx1JdwKBgCZQBwTx8HcbAXkWPAZAAfRwrYzRkKNlh4a4JSgeQpW-eNilKco9Q6OhDwQF0vHsa0CAfWx7CcSQglgeDxShe9tWMAA1NAEEMMgpFGINdjDNkI0vBICAk1ppOwuTgwwRT2QAXlZdkADJQAAb1APCCOkIEACI-T5bSQwABS8Zh1Kk8soFs0AAF8AG4UTAbtN0WR9n2MZR+C-LMHxPc0fjnIyI0wK4JHEyTNNk+TdJzUAvR2TUVmQmAoKKH5lmgGASwjMjliYYpr2pAArJ9mBwshFiRHCQnCSJogYBr+jiTBMjwS9wOHCdPLIBz3Cc5hDKjJAdKBYSIxo-SAD5zNEb1JuYewXXeDysoW0BDJW3Y-F+cE3DwKNgAAHQAHmABxClswATIls+NAu9X4ck+IgWNdU6mC0nLJDocGZIWvSI0CgKgtACsYCKRr+QsX4IenaKS0lOgSjKDh-zCyVUCwSRGzwaIgjMAMoDwDGFyQcVVMKaQqqKgh+yZvJ0HWhwfAmwnmBQt8KzWC7QCjFAqCBWHIZ0hGHE2nazL28jLhtVAYAcOW1j+0RkaCe0AydCk8EKFZfhGy59FjZALWgnTp1nQCn3+Qo71qiRlk8XgHA4MdpukskuZORReXZNA9aKbDUtAXlkKUmT3VEA7XZDQzbLQf4MCjGIthgLYtipjBkA4wgYnjWzAqzsOIeyt3DKb2b-QW5acuNiWpSlqgo3b5XdmNoIAHkYOK6rbdARg5UKHBuPvYr+DhYeZCF1Kgj7jAB4IMn0DyHgWTPF0EHeC33E8dwM93-fu50seJCecxexxmRT3gFC8BWWgEC0DAeQ7hZAIGZkeE4SoVAWl+FKYoyASBJw8NQMgVVFzsy4MSF8MgTgIHcEEE8RY4SIWUExKeaQAAsAAGKhEo4BUDgXrFKABxfoAAJXgWx6iEBEO6EAQR6AbBwIQAEIAHBbk4X4M+wAACyZRPCXGUBgYAoR8ARDZNEYAPAeG+GAAAJioXoj06U5QMDSDgNy9RAIOBxodbkep3BYD4cAARQiREgEQOwNAAAvfOdwEBSPgMAVmS4ES4CRHCJAYT1D9WUaIIAA)