# Class Decomposition

When a TypeScript definition file contains an interface and a variable with the same name, this is called *class decomposition*. Additionally, a second interface may modify the class further. One interface may define the *instance side* members of the class, and the other may define the *static side*.

	interface Function {
		apply(thisArg: any, argArray?: any): any;
		call(thisArg: any, ...argArray: any[]): any;
		bind(thisArg: any, ...argArray: any[]): any;

		prototype: any;
		length: number;

		// Non-standard extensions
		arguments: any;
		caller: Function;
	}

	interface FunctionConstructor {
		new (...args: string[]): Function;
		(...args: string[]): Function;
		prototype: Function;
	}

	declare var Function: FunctionConstructor;
	
## Order of declarations

TypeScript's `lib.d.ts` seems to always declare the interface first, before the variable, like in the example above.

However, DefinitelyTyped's [`node.d.ts`](https://github.com/borisyankov/DefinitelyTyped/blob/16c494b98619ae7aace3226f6d542a56e23109c7/node/node.d.ts) proves that this order is not required. The `ucs2` type in the `"punycode"` module is a decomposed class where the variable is declared before the interface.

	declare module "punycode" {
		export var ucs2: ucs2;
		interface ucs2 {
			decode(string: string): string;
			encode(codePoints: number[]): string;
		}
	}
	
## Further Reading

[TypeScript Handbook: Writing Definition Files](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)
