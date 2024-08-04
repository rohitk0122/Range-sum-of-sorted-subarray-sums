# Range-sum-of-sorted-subarray-sums
class Solution {
    public int rangeSum(int[] nums, int n, int left, int right) {
          int MOD = 1_000_000_007;
        List<Integer> subarraySums = new ArrayList<>();
        
        // Generate all possible sums of non-empty continuous subarrays
        for (int i = 0; i < n; i++) {
            int currentSum = 0;
            for (int j = i; j < n; j++) {
                currentSum += nums[j];
                subarraySums.add(currentSum);
            }
        }
        
        // Sort the sums
        Collections.sort(subarraySums);
        
        // Calculate the sum from index left to index right (1-based index)
        long result = 0;
        for (int i = left - 1; i < right; i++) {
            result = (result + subarraySums.get(i)) % MOD;
        }
        
        return (int) result;
    }
}
