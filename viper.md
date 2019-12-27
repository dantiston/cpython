# Intro
Viper is a compiled, statically typed, Python-like language building on the official type annotation syntax in PEP 484 and PEP 526. The initial thought is to compile to Java bytecode.

# Goals
* Provide static type-checking
* Significantly improve Python performance

## Non-Goals
* Support all of Python, especially duck typing
* Multi-threading support

# Features
* Compile a subset of Python code into an executable binary
    * The subset of supported Python code is approximately
        * Type annotated Python, e.g. parameters, variables, and members
        * Python where types can be inferred
* Type inference
    * Literals, object instantiations, function calls, and return types have their types inferred, meaning more performance for less work
* Type refinement
    * Explicit type-checks refine the type of a variable at compile time
        * `if type(a) == int: ... else: ...`
        * `assert type(a) == int`
        * `if isinstance(a, int): ... else: ...`
        * `assert isinstance(a, int)`

## Unsupported Python features
* duck typing
    * `a = 3; a = 'abc'` throws a `TypeError`

# Plan
1. Utilize the existing `ast` module as lexer + parser
1. Compile `ast` responses to bytecode (???)
1. Provide custom lexer + parser to replace `ast`

# Notes
This project is similar to Cython, but instead of using custom syntax, embraces the official type annotation syntax.
This project goes beyond `mypy` to compile Python into an executable binary.
