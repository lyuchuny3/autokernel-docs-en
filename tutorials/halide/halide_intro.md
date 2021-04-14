# Introduction to Halide   
Halide is a domain-specific language for vision and image processing algorithms and allows programmers to author efficient image processing pipelines. Halide separates the program into two conceptual parts:    
■ The algorithm – Defines what is computed at each pixel  
■ The schedule – Defines how the computation should be organized

Every Halide program must consist of these two parts, and the user specifies both of them. The following example is a horizontal blur program authored in Halide:
```
// Image with 8 bits per pixel.  
ImageParam input(UInt(8), 2) Halide::Func f;    
// Algorithm.   
f(x, y) = (input(x-1, y) + input(x, y) + input(x+1, y))/3;    
// Schedule   
f.hexagon().vectorize(x, 8).parallel(y, 16);  
```
The algorithm concisely defines the blur computation in terms of the x and y coordinates of a pixel. The schedule directs how the computation should be conducted. In this instance, the programmer has directed Halide to vectorize the blur algorithm by a factor of 8 pixels, parallelize the algorithm by a factor of 16, and launch it on the Hexagon HVX processor.

The Halide HVX compiler automatically translates the high-level image algorithm written by the programmer into an efficient HVX executable.
The Halide community has a rich set of tutorials hosted at [here](https://halide-lang.org/tutorials/tutorial_introduction.html). An in-depth explanation of the different features of the language is beyond the scope of this document. However, this section presents a high-level introduction to some of the important features of the language.
