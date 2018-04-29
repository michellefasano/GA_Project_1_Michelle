# GA_Project_1_Michelle

Problem 1:

def palindrome_checker(number):
    #get the full number as as string then compare it to the number printed backwards
    if str(number)[0:] == str(number)[::-1]:
        result = True
    else:
        result = False
    return result
    #if the two are equal - then its a palindrome so the result should be true

#checking that it works
palindrome_checker(1331)

#creating two data sets with all 3 digits integers so that each combination can be multiplied 
three_digit_list1 = range(100,1000)
three_digit_list2 = range(100,1000)

for number1 in three_digit_list1:
    #iterate on all the combinations of two 3-digit numbers being mutiplied
    for number2 in three_digit_list2:
        product = number1 * number2
        #feed the result through the palindrome checker
        if palindrome_checker(product):
            print(product)

#then print all the  palindromes and the last one to print will be the largest. answer is 266662

Problem 2:
#create two sets of numbers in order to iterate using a for loop - one set to divide into the other
number_list1 = range(2,2000)
number_list2 = range(2,2000)

#create placeholder/container for the prime numbers. The results list is just so I can see what's happening if needed

results = []
prime_list = []

#iterate on the the list of numbers, dividing all numbers from the second set into the first - if there is nothing which divides evenly, it is a prime. We can track this by counting how many results have zero as the result of %. All numbers are divisible by 1, so we start the data set at 2
for number1 in number_list1:
    mult_counter = 0
    for number2 in  number_list2:
        answer = number1%number2
        results.append(answer)
        if answer == 0:
            mult_counter = mult_counter + 1
    #each prime number will divide into itself, so there will be one instance of % = 0, but if the counter counts any more than 1, it is not a prime number
    if mult_counter == 1:
        prime_list.append(number1)
        
print(prime_list)
sum(prime_list)

Problem 3:
#create container to hold all the multiples of 3 and 5 under 1000
multiples_list = []

#the range function lets us get the full data set we will be testing
integers_under_1000 = list(range(1,1000))
for number in integers_under_1000:
    
    #the % operator lets us check for divisibility on 3 OR 5 - then we can add it to the container we created if it meets the criteria
    if number%3 == 0 or number%5 == 0:
        multiples_list.append(number)
    
print(multiples_list)
sum(multiples_list)

Problem 4:
#this one was hard! 
#first we define the function. 
def string_compressor2(string):
    
    #we know we want the result to be a string, so we can define that result as an empty string upfront then add to it as we go throguh each step
    results = ""
    
    #we need to count how many characters in a row are the same - starting with 1 not zero because a standalone character is still one
    char_counter = 1
    #start filling up the result string with the first character
    results += string[0]
    
    #interate on each character in the string, but stopping with one short, to make sure the +1 doesn't cause an out of range error
    for n in range(len(string)-1):
        #if the character is the same as the character after it, then start tallying how many are in a row by adding one, will repeat this until a new character starts
        if (string[n] == string[n+1]):
            char_counter += 1
        
        #before a new character starts, we need to add the string of the counter and the next character to our result string
        else:
            if char_counter >= 1:
                results += str(char_counter)
            results += string[n+1]
            char_counter = 1
    
    #once the interation is done, we need to add the last count
    if char_counter > 1:
            results += str(char_counter)
    #we only want to print the compressed string if its shorter in length than the original
    if len(results) > len(string):
        return string
    else:
        return results  

string_compressor2("hellloooo") 

Problem 5:
#we need to print from 1 to 100 inclusive, so the range goes to 101
fizzbuzz = range(1,101)
#we want the result of the program to be a list, so we create that empty list first
fizzbuzz_printer = []

#we want to iterate on all the numbers in the range, checking first for divisibility of both 3 and 5. So that we don't print an extra fizz or buzz, we use the elif function to just check for 3 adn 5 separately, if the number is not divisble by both. after each statement, we append the proper string to the list. if nothing works, then we just append the number itself
for number in fizzbuzz:
    if number%3 == 0 and number%5 == 0:
        fizzbuzz_printer.append("FizzBuzz")
    elif number%5 == 0:
        fizzbuzz_printer.append("Buzz")
    elif number%3 == 0:
        fizzbuzz_printer.append("Fizz")
    else:
        fizzbuzz_printer.append(number)

print(fizzbuzz_printer)
