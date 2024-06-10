from itertools import combinations_with_replacement 

"""
Input value
n : index of the icosahedral/dodecahedral number

Return value: the n-th icosahedral/dodecahedral number
"""
def make_icosahedral(n):
    return int(5/2*n**3-5/2*n**2+n)

def make_dodecahedral(n):
    return int(9/2*n**3-9/2*n**2+n)

"""
Input values
    m : maximum value of the positive integers that we are checking
    n : index of the largest icosahedral/dodecahedral number we are using to compute the sums
    limit: the maximum number of icosahedral/dodecahedral numbers in the sum
    threshold: the threshold for m

Return value: a list of positive integers between 2000 and f(n) that CANNOT be represented as at most "limit"
              numbers of icosahedral/dodecahedral numbers.
"""

def sum_of_icosahedrals(m, n, limit, threshold):
    numbers_up_to_m = list(range(threshold, m)) 
    for j in combinations_with_replacement(map(make_icosahedral, list(range(n + 1))), limit):
        if sum(j) in numbers_up_to_m:
            numbers_up_to_m.remove(sum(j))
    return numbers_up_to_m

def sum_of_dodecahedrals(m, n, limit, threshold):
    numbers_up_to_m = list(range(threshold, m)) 
    for j in combinations_with_replacement(map(make_dodecahedral, list(range(n + 1))), limit):
        if sum(j) in numbers_up_to_m:
            numbers_up_to_m.remove(sum(j))
    return numbers_up_to_m

"""
Want to show: For any integer m such that 2000 <= m < 6860, m can be written as a sum of at most 8 
              icosahedral numbers.
              For any integer m such that 2000 <= m < 5290, m can be written as a sum of at most 14 
              dodecahedral numbers.

For icosahedral numbers, the largest icosahedral number we can take is the 13th icosahedral number.
Therefore, take n = 13, limit = 8, and threshold = 2000.

For dodecahedral numbers, the largest dodecahedral number we can take is the 10th dodecahedral number.
Therefore, take n = 10, limit = 14, and threshold = 2000.
"""
sum_of_icosahedrals(6860, 13, 8, 2000) #actual return value: []

sum_of_dodecahedrals(5290,10,14,2000) # actual return value: []
