# G-P-M in Go

We all know that goroutine is used in golang instead of the original kernal thread ,which uses less memory.

> Normally ,the thread stack requires 2M place, but the gouroutine stack only requires 2K place.

Golang's resource scheduler model is called GPM model, where G stands for Goroutine, P for Processor and M for Machine. 

Machine is the kernal thread which actually run the program code. The number of  Machine is not fixed, but generally less than 10000.

Each Goroutine has a G-struct bind to it which stores the task function, stack information,  running status . G-struct is reusable

Processor is responsible for scheduling different Goroutines to run on Machine. For a Goroutine ,the Processor is the "CPU" that actually runs the logical ,while for a Machine ,the Processor provides the goroutine queue and running context. The number of Processor determines the maximum number of the parallel goroutine operations.

The following is a cartoon showing how the GPM model works:

![](.gitbook/assets/image%20%281%29.png)

The bricks in the diagram above are Goroutines, and we can also see there are many bricks ,which  means that programer can easily create many goroutines and run them.

The gophers are Machines , which are the actually worker to transport the bricks.

The cart is the Processor, which decides which gopher carries which brick. If a processor has no free Machine to use ,a new Machine will be created.

### References

1. [https://www.zhihu.com/question/21409296/answer/1040884859](https://www.zhihu.com/question/21409296/answer/1040884859)

