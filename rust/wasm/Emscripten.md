# Emscripten
a toolchain to convert C/C++ code into a WebAssembly module
## commponents
- Emscripten compiler frontend (emcc)
- Emscripten SDK (emsdk)
## install
> https://github.com/emscripten-core/emsdk
## .emscripten 
the Emscripten configuration file

# LLVM IR
LLVM intermediate representation

# emcc
the compiler frontend that converts C/C++ into LLVM IR (both binary and 
human-readable form) and into the WebAssembly binary or arm.js.

# emsdk
helps manage and maintain the Emscripten toolchain commponents and set up the 
runtime/terminal environment to run emcc.

--------------------------------------------------------------------------------
# generate asm.js
```cpp
/* sum.cpp */
extern "C" {
	unsigned sum(unsigned a, unsigned b) {
		return a + b;
	}
}
```
> emcc -O1 ./sum.cpp -o sum.html -sWASM=0 -sEXPORTED_FUNCTIONS='["_sum"]'
- -O1       less-optimized code
- -o        provide the desired name for the output
- -s        takes in a key and value as their arguments
(The emcc compiler generates the WebAssembly module by default)
- WASM=0    instruct the compiler to generate asm.js like JavaScript instead of
            WebAssembly
- EXPORTED_FUNCTIONS        specify the exported functions

--------------------------------------------------------------------------------
# WebAssembly Modules (WASM)
- WebAssembly is a virtual instruction set architecture

# WAST
human-readable format of the WebAssembly binary
# s-expression format
Every instruction/expression in s-expression syntax should live within a pair
of parentheses, ().
- The textual format is an s-expression format
- s-expression are commonly used when defining a nested list or structured tree
