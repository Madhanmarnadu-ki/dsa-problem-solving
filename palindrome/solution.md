public class Solution
{
    // Checks whether an integer is a palindrome without converting to string.
    // Time:  O(d), where d = number of digits
    // Space: O(1)
    public bool IsPalindrome(int x)
    {
        // Negative numbers can't be palindromes (they start with '-'),
        // and any non-zero number ending with 0 can't be a palindrome
        // because palindromes can't start with 0.
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;

        int rev = 0; // Will hold the reversed "right half" of the number

        // Build 'rev' from the last digits of x until we've processed half the digits.
        // When x <= rev, we've consumed at least half of the digits.
        while (x > rev)
        {
            // Append the last digit of x to rev
            rev = rev * 10 + (x % 10);

            // Drop the last digit from x
            x /= 10;
        }

        // For even digit counts: x == rev
        // For odd digit counts: middle digit is in 'rev', so compare x with rev/10
        return x == rev || x == rev / 10;
    }
}
