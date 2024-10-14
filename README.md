# Lecture 6

## Lambda Expression

Lambda expression is just a shortcut to define an implementation of a functional interface (referring to interfaces with only one abstract method such as Runnable/Comparator)

Syntax for lambda expression:

- (parameters) -> expression
- (parameters) -> { statements } **[if body contains more than one statement]**

Defining functional interface:

@FunctionalInterface
interface MyFunction {
void print(String message);
}

## <span style="color:blue">Streams</span>

Stream Pipeline: A stream pipeline consists of:

**Source:** Where the data comes from (e.g., a collection like a List, an array, or an I/O channel).

**Intermediate Operations:** Transform the stream into another stream (e.g., filter(), map()). These operations are lazy, meaning they don’t execute until a terminal operation is invoked.

**Terminal Operations:** Produce a result or a side effect (e.g., collect(), forEach()). Terminal operations trigger the execution of the pipeline.

**Syntax of a stream**

List<String> names = Arrays.asList("John", "Jane", "Jack", "Doe");

// Using streams to filter, map, sort, and collect
List<String> result = names.stream()
.filter(name -> name.startsWith("J")) // Filter names that start with "J"
.map(String::toUpperCase) // Convert to uppercase
.sorted() // Sort alphabetically
.collect(Collectors.toList()); // Collect to a list

System.out.println(result); // Output: [JACK, JANE, JOHN]

### Parallel Streams `#RRGGBB`

Parallelizing streams in Java refers to breaking up a stream of data into multiple chunks and processing them concurrently using multiple threads, typically leveraging multi-core processors. This allows for faster data processing by dividing the workload across different threads, potentially reducing the overall execution time for large datasets.

Key Concepts of Parallel Streams:

    •	Automatic Parallelization: Java’s parallel streams handle parallel execution automatically. You don’t need to manually manage threads or synchronization. The parallel stream splits the data into multiple parts, processes them concurrently, and then merges the results at the end.
    •	Data Partitioning: When you use a parallel stream, the data is divided into chunks that are processed independently on different threads.
    •	Fork/Join Framework: Internally, parallel streams use the Fork/Join Framework, which allows multiple tasks to be split, executed in parallel, and then joined back together once completed.
