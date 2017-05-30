# lcm

least common multiple (asm80)
(go to raw version of readme.md file to see formatted code)
This program is calculating lcm. You can compile and try it here: http://www.asm80.com/
LCM is the smallest positive integer that is divisible by both a and b.
To calculate it I used reduction by greatest common divisor (GCD - is the largest positive integer that divides each of the integers).
To calculate GCD i used subtraction-based version of Euclidean algorithm (https://en.wikipedia.org/wiki/Euclidean_algorithm)
a, b - input numbers
int gcd(int a, int b){
  while (a != b){
    if (a > b)
      a = a - b;
    else
      b = b - a;
  }
  return a
}

With gcd I was able to calculate LCM:
int lcm = a*b/gcd(a,b)

Intel8080 has no multiplication / division instructions (see assembler_model.pdf) so i had to use multiplication by addition and division by subtraction. 

Multiplication by addition:
example: 3*4=12
int a = 3; // first number
int b = 4; // second number, counter
result=0 
while (n != 0) {
  result = result + a;
  b = b - 1;
}

Division by subtraction:
example: 15/5=3
int a = 15; 
int b = 5;
int result = 0;
while (a > 0){
  a = a - b;
  result = result + 1;
}

