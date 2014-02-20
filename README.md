# NumericIntegration

Parallel Numeric Integration for julia.

Very simple implementation using the trapezoid rule.  Takes advantage of any available workers when computing the area of each
trapezoid.  The function takes the function who's integral is to be estimated, the boundaries, the absolute maximum of the 
second derivitive of the function within the boundaries and the desired upper error bound. The result and number of trapezoids
used to compute is returned.

Example usage:

julia -p 8

using NumericIntegration

@everywhere f(x) = 1 - x^2
a = 0
b = 1
k = 2
er = .0001

trapezoidal(f, a, b, k, er)
(0.6665675193337299,41)

Note for performance use the optimal quadgk() function in the standard library.
