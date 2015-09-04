# Class Decomposition

When a TypeScript definition file contains one or more interfaces and a variable that all have the same name, this is called *class decomposition*.

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
	
## Further Reading

[TypeScript Handbook: Writing Definition Files](https://github.com/Microsoft/TypeScript-Handbook/blob/master/pages/Writing%20Definition%20Files.md)
