# python
import math

def velocity(t):
    g = 9.8
    m = 68.1
    c = 12.5
    return (g * m / c) * (1 - math.exp(-(c / m) * t))

def distance(t, n):
    a = 0  # Lower limit of integration
    b = t  # Upper limit of integration
    h = (b - a) / n  # Width of each segment

    # Calculate the sum of the function values at the segment endpoints
    sum = velocity(a) + velocity(b)

    # Calculate the sum of the function values at the segment midpoints
    for i in range(1, n):
        x = a + i * h
        sum += 2 * velocity(x)

    # Calculate the final result using the trapezoidal rule formula
    result = (h / 2) * sum
    return result

# Test the distance function with different numbers of segments
t = 10  # Time in seconds
segments = [10, 100, 1000, 10000]

for n in segments:
    d = distance(t, n)
    print(f"Number of segments: {n}, Distance: {d} meters")
