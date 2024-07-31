# Sock Merchant Problem - HackerRank Problem

This repository contains a solution to the Sock Merchant problem from HackerRank. The problem involves finding the number of matching pairs of socks from a given list.

## Problem Statement

You are given a list of integers representing the colors of socks. Your task is to determine how many pairs of socks with matching colors there are.

### Function Signature

```csharp
public static int sockMerchant(int n, List<int> ar)
```
- `n` (INTEGER): The number of socks in the list.
- `ar` (INTEGER_ARRAY): The list of integers representing the colors of the socks.
### Example
Input:

makefile
```
n = 9
ar = [10, 20, 20, 10, 10, 30, 50, 10, 20]
```
Output:

`3`
### Explanation:

There are three pairs of socks:

A pair of socks with color 10
A pair of socks with color 20
Another pair of socks with color 10
Solution
The solution involves counting the occurrences of each color and then determining how many pairs can be formed from the counts.

``` csharp
Copiar código
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;

class Result
{
    /*
     * Complete the 'sockMerchant' function below.
     *
     * The function is expected to return an INTEGER.
     * The function accepts following parameters:
     *  1. INTEGER n
     *  2. INTEGER_ARRAY ar
     */

    public static int sockMerchant(int n, List<int> ar)
    {
        Dictionary<int, int> sockCounts = new();
        foreach (int sock in ar)
        {
            if (sockCounts.ContainsKey(sock))
            {
                sockCounts[sock]++;
            }
            else
            {
                sockCounts[sock] = 1;
            }
        }
        
        int pairs = 0;
        foreach (int count in sockCounts.Values)
        {
            pairs += count / 2;
        }

        return pairs;
    }
}

class Solution
{
    public static void Main(string[] args)
    {
        TextWriter textWriter = new StreamWriter(@System.Environment.GetEnvironmentVariable("OUTPUT_PATH"), true);

        int n = Convert.ToInt32(Console.ReadLine().Trim());

        List<int> ar = Console.ReadLine().TrimEnd().Split(' ').ToList().Select(arTemp => Convert.ToInt32(arTemp)).ToList();

        int result = Result.sockMerchant(n, ar);

        textWriter.WriteLine(result);

        textWriter.Flush();
        textWriter.Close();
    }
}
```
## How to Run
Compile the code: Ensure you have the .NET SDK installed on your machine.

Run the code: Use the following command to run the program:

sh
```
dotnet run
```

Input: Provide the input through the console or by setting the OUTPUT_PATH environment variable to specify the output file.
