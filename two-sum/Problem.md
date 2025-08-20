using System.Collections.Generic;

public class Solution
{
    /// <summary>
    /// Two Sum: return indices of two numbers that add up to target.
    /// Complexity: Time O(n), Space O(n).
    /// </summary>
    public int[] TwoSum(int[] nums, int target)
    {
        // Map each value we've seen -> its index
        var seen = new Dictionary<int, int>();

        // Walk the array once
        for (int i = 0; i < nums.Length; i++)
        {
            // The partner value we need to reach 'target' with nums[i]
            int need = target - nums[i];

            // If we've already seen the partner value, we found a valid pair
            if (seen.TryGetValue(need, out int idx))
            {
                // Return indices: first the index where 'need' was seen, then current i
                return new[] { idx, i };
            }

            // Otherwise remember the current value's index for future elements
            // This lets a future element equal to 'need' match with nums[i]
            // Overwriting the index on duplicates is fine for standard Two Sum
            seen[nums[i]] = i;
        }

        // If no pair exists: return empty (LeetCode usually guarantees one answer)
        return System.Array.Empty<int>();
    }
}
