# Three-sum-leet
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = []
        nums.sort()  # Sorting makes it easy to skip duplicates and use pointers

        for i, a in enumerate(nums):
            # Skip the same value for 'a' to avoid duplicate triplets
            if i > 0 and a == nums[i - 1]:
                continue
            
            l, r = i + 1, len(nums) - 1
            while l < r:
                threeSum = a + nums[l] + nums[r]
                
                if threeSum > 0:
                    r -= 1  # Sum is too big, move the right pointer in
                elif threeSum < 0:
                    l += 1  # Sum is too small, move the left pointer in
                else:
                    # Found a triplet!
                    res.append([a, nums[l], nums[r]])
                    
                    # Now we must move the left pointer and skip duplicates for 'l'
                    l += 1
                    while nums[l] == nums[l - 1] and l < r:
                        l += 1
                        
        return res
