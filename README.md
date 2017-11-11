# llvm-scratchpad

## starting

```cpp
static LLVMContext TheContext;
static IRBuilder<> Builder(TheContext);
static std::unique_ptr<Module> TheModule;
static std::map<std::string, Value *> NamedValues;

Value *LogErrorV(const char *Str) {
  LogError(Str);
  return nullptr;
}

```

 * `LLVMContext`: Opaque object owns a lot of core LLVM data structures. Type and Constant Value tables. A single instance for our case to pass into APIs that require it.  
 * `IRBuilder`: Apparently makes easy to generate LLVM Instructions
 * `Module`: Contains functions and global variables. Container for code. All memory owned by this, and values we generate are pointers to memory in here.
 * `NamedValues`: Tracks names in scope, also LLVM representation.


## Integers

There must already be a class in AST through visitor pattern which holds an integer. 
[ConstantInt](http://llvm.org/doxygen/classllvm_1_1ConstantInt.html) 

```cpp
/* codegen */
ConstantInt::get(_context, APInt(value))
```

## Instruction

## BasicBlock

## Function

## Order

- [ ] Declarations
    - [ ] Integer
    - [ ] IntArray
- [ ] Codeblock
    - [ ] Assignment

# Resources

* [Example driver code](https://opensource.apple.com/source/lldb/lldb-69/llvm/examples/ModuleMaker/ModuleMaker.cpp?txt)
