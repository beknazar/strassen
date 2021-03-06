## Optimization of Strassen's algorithm for when n &#8800; 2^k

** Padding zeros approach is used **

This contains a relatively simple sample implementation of the Strassen Algorithm for matrix multiplication, written in C++. Also provided are some wrapper classes for matrices and other matrix multiplication methods which can be used for comparison.

See http://en.wikipedia.org/wiki/Strassen_algorithm or section 28.2 of CLRS for more information on the algorithm.

Most of the functionality is implemented in templated header files, under src/strassen. There is a test source file at src/test/test_strassen_matrix.cpp demonstrating how to use the matrix wrapper classes and the matrixm multipliers.

A matrix<T> object uses a matrix_multiplier<T> object to perform its matrix multiplication. This defaults to the strassen_matrix_multiplier<T>, but can be customized by passing a different type to the matrix constructor. For example,

strassen::matrix<int> A (123, 456); // Default strassen_matrix_multiplier<int>
strassen::matrix<int> B (123, 456, new strassen::parallel_strassen_matrix_multiplier<int> ()); // Uses custom matrix multiplier
A.mult (B) // A now equals A * B
