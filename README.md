# Generate-all-Combinations-of-Balanced-Parentheses-in-C

All Combinations of Balanced Parentheses in C
Today in this article we will discuss the program to generate all combinations of balanced parentheses in C+programming language. We are given an integer N representing the number of pairs of parentheses, the task is to generate all combinations of well-formed(balanced) parentheses.

Generate all Combinations of Balanced Parentheses in C
Example
Input : n=2
Output:
{}{}
{{}}
Explanation:
This the only two sequences of balanced parenthesis formed using 2 pair of balanced parenthesis.
Algorithm :
Create a recursive function that takes a string (s), the number of opening and closing brackets (o and c), and the value of n.
If the opening and closing bracket values are both equal to n, print the string and return.
If the number of opening brackets is larger than the number of closing brackets, use the following parameters to call the function recursively.
Count of the opening bracket o, count of the closing bracket c + 1, and n.
If the number of opening brackets is fewer than n, use the following parameters to call the function recursively.
If the count of opening bracket is less than n then call the function recursively with the following parameters String s + “{“, count of opening bracket o + 1, count of closing bracket c, and n.
Code in C
Run
#include <stdio.h>
#define MAX_SIZE 100
 
void _printParenthesis(int pos, int n, int open, int close);

void printParenthesis(int n)
{
    if (n > 0)
        _printParenthesis(0, n, 0, 0);
    return;
}
 
void _printParenthesis(int pos, int n, int open, int close)
{
    static char str[MAX_SIZE];
 
    if (close == n) {
        printf("%s \n", str);
        return;
    }
    else {
        if (open > close) {
            str[pos] = '}';
            _printParenthesis(pos + 1, n, open, close + 1);
        }
 
        if (open < n) {
            str[pos] = '{';
            _printParenthesis(pos + 1, n, open + 1, close);
        }
    }
}

int main()
{
    int n = 3;
    printParenthesis(n);
    getchar();
    return 0;
}
Output :
{}{}{} 
{}{{}} 
{{}}{} 
{{}{}} 
{{{}}} 
