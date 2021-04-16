# Introduction to Halide   

Halide is an open source, domain specific language (DSL) designed to make it easier to write high-performance image and array processing code on modern machines.

## Embedded in C++
Halide is a domain specific language (DSL) embedded in C++. This means you write C++ code that builds an in-memory representation of a Halide pipeline using Halide's C++ API.

## Decouple algorithm from schedule
Halide separates the program into two conceptual parts:
- The algorithm – Defines what is computed at each pixel
- The schedule – Defines how the computation should be organized 
Through this design, developers can focus on how to implement their algorithm in isolation from how it should be best scheduled for execution, to optimize for locality, parallelism, and ultimately performance.

## Compile
An image processing C++ pipeline using Halide must first be compiled. This is done by the Halide compiler that uses an LLVM compiler to generate a platform-specific runtime executable. Halide offers two modes to perform this compilation:

- Ahead of Time (AOT): Halide is first compiled to a header and object file and then statically linked by the developer into their app.
- Just in Time (JIT): performs compilation at runtime (i.e., while the app is running) but requires that the Halide compiler be hosted on the target platform.

AOT is generally preferred because it avoids the overhead of runtime compilation, uses a smaller binary (because developers don’t need to host the whole Halide compiler), and includes its own C runtime. AOT is therefore commonly used for mobile platforms.

The main benefit of the Halide compiler for developers is that it generates a platform-specific runtime, capable of optimizing image processing pipelines for specific platforms. This also reduces the need for developers to have specialized knowledge and skills for that platform’s hardware to make optimizations. Instead the developer can focus on high-level algorithmic design and schedules.

## Target
Halide currently targets:

- CPU architectures: X86, ARM, MIPS, Hexagon, PowerPC, RISC-V
- Operating systems: Linux, Windows, macOS, Android, iOS, Qualcomm QuRT
- GPU Compute APIs: CUDA, OpenCL, OpenGL Compute Shaders, Apple Metal, Microsoft Direct X 12

## Resources
- github:https://github.com/halide/Halide
- For API doc, see http://halide-lang.org/docs

Ref:
1. https://halide-lang.org/
2. https://developer.qualcomm.com/blog/optimizing-image-processing-algorithms-halide

    
