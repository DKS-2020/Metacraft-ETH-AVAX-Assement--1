## ErrorHandling Smart Contract:

### Overview:
This Solidity smart contract provides functions for basic arithmetic operations with robust error handling using require(), assert(), and revert() statements.

### Description :
The ErrorHandling contract includes functions for division, addition, subtraction, and multiplication. Each function incorporates error handling to ensure operations are executed correctly and securely:
1. Division: Ensures the denominator is not zero and that the numerator is divisible by the denominator.
2. Addition: Requires both numbers to be greater than zero and asserts that the result does not overflow.
3. Subtraction: Checks that both numbers are greater than zero and that the subtraction does not result in a negative value.
4. Multiplication: Ensures both numbers are greater than zero and verifies the result using assert to prevent overflow.

#### Mapping Variable:
balances: Maps addresses to their respective token balances.

### Author:
https://github.com/DKS-2020

### License:
This project is licensed under the MIT License - see the LICENSE.md file for details

### Smart Contract Code:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ErrorHandling {
    function Division(uint numerator, uint denominator) public pure returns (uint) {
        require(denominator != 0, "Denominator cannot be zero");
        if (numerator % denominator != 0) {
            revert("Numerator must be divisible by denominator");
        }
        return numerator / denominator;
    }

    function add(uint a, uint b) public pure returns (uint) {
        require(a > 0 && b > 0, "Both numbers must be greater than 0");
        uint result = a + b;
        assert(result >= a);
        return result;
    }

    function subtract(uint a, uint b) public pure returns (uint) {
        require(a > 0 && b > 0, "Both numbers must be greater than 0");
        require(a >= b, "Subtraction result cannot be negative");
        return a - b;
    }

    function multiply(uint a, uint b) public pure returns (uint) {
        require(a > 0 && b > 0, "Both numbers must be greater than 0");
        uint result = a * b;
        assert(a == 0 || result / a == b);
        return result;
    }
}

