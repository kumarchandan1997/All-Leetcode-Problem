# Important Leet Code Problem

### 1. 217. Contains Duplicate

Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.

```php
$nums = [1,2,3,1];
    
    function containsDuplicate($nums) {

        $seen = [];

        foreach ($nums as $num) {
            if (isset($seen[$num])) {
                return true;
            }
            $seen[$num] = true;
        }

       return false;   
    }
```

### 2. 242. Valid Anagram

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

Input: s = "anagram", t = "nagaram"

Output: true

```php
   function isAnagram($s, $t) {
        $stringlen1=strlen($s);
        $stringlen2=strlen($t);
        if($stringlen1  != $stringlen2)
        {
            return false;
        }
        $sortArray1 = str_split($s);
        sort($sortArray1);
        $finalstring1=implode('',$sortArray1);
        $sortArray2= str_split($t);
        sort($sortArray2);
        $finalString2 = implode('',$sortArray2);
        if($finalstring1 === $finalString2)
        {
            return true;
        }
        
        return false;
        
    }
```

### 3. 1. Two Sum

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

```php
     function twoSum($nums , $target)
     {
        $map =[];
        foreach($nums as $index => $num){
            $complement = $target-$num;
            
            if(isset($map[$complement]))
            {
                return [$map[$complement],$index];
            }
            
            $map[$num] =$index;
        }
        return null;
    }
    $nums = [2, 7, 11, 15];
    $target = 17;
    
    $result = twoSum($nums, $target);
    print_r($result);
```

### 4. 1491. Average Salary Excluding the Minimum and Maximum Salary

You are given an array of unique integers salary where salary[i] is the salary of the ith employee.
Return the average salary of employees excluding the minimum and maximum salary. Answers within 10-5 of the actual answer will be accepted.
Example 1:

Input: salary = [4000,3000,1000,2000]
Output: 2500.00000
Explanation: Minimum salary and maximum salary are 1000 and 4000 respectively.
Average salary excluding minimum and maximum salary is (2000+3000) / 2 = 2500

```php
     function average($salary) {
        $n = count($salary);
        $arraySum = array_sum($salary);
        $minSalary = min($salary);
        $maxSalary = max($salary);
        $finalSalary = $arraySum-($minSalary+$maxSalary);


        $average = $finalSalary/($n-2);

         return number_format($average,5,'.','');
    }
```

### 5. 1523. Count Odd Numbers in an Interval Range

Given two non-negative integers low and high. Return the count of odd numbers between low and high (inclusive).
Example 1:

Input: low = 3, high = 7
Output: 3
Explanation: The odd numbers between 3 and 7 are [3,5,7].

```php
     function countOdds($low, $high) {
        return intval(($high + 1) / 2) - intval($low / 2);
    }
```

### 6. 283. Move Zeroes

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.
Note that you must do this in-place without making a copy of the array.
Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]

```php
     function moveZeroes(&$nums) {
         $n = count($nums);
        $nonZeroIndex = 0;

        for ($i = 0; $i < $n; $i++) {
            if ($nums[$i] != 0) {
                $nums[$nonZeroIndex++] = $nums[$i];
            }
        }


        for ($i = $nonZeroIndex; $i < $n; $i++) {
            $nums[$i] = 0;
        }
    }
```

### 7. 88. Merge Sorted Array

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.
Merge nums1 and nums2 into a single array sorted in non-decreasing order.
The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.
Example 1:

Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```php
    function merge(&$nums1, $m, $nums2, $n) {
        $i = $m - 1; 
        $j = $n - 1; 
        $k = $m + $n - 1; 

        while ($i >= 0 && $j >= 0) {
            if ($nums1[$i] > $nums2[$j]) {
                $nums1[$k] = $nums1[$i];
                $i--;
            } else {
                $nums1[$k] = $nums2[$j];
                $j--;
            }
            $k--;
        }

        while ($j >= 0) {
            $nums1[$k] = $nums2[$j];
            $j--;
            $k--;
        }
    }
```

### 8. 238. Product of Array Except Self

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
You must write an algorithm that runs in O(n) time and without using the division operation.
Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```php
    function productExceptSelf($nums) {
         $n = count($nums);
        $result = array_fill(0, $n, 1);

        
        $leftProduct = 1;
        for ($i = 0; $i < $n; $i++) {
            $result[$i] = $leftProduct;
            $leftProduct *= $nums[$i];
        }

        
        $rightProduct = 1;
        for ($i = $n - 1; $i >= 0; $i--) {
            $result[$i] *= $rightProduct;
            $rightProduct *= $nums[$i];
        }

        return $result;
    }
```

### 9. 121. Best Time to Buy and Sell Stock

You are given an array prices where prices[i] is the price of a given stock on the ith day.
You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```php
    function maxProfit($prices) {
        $minPrice = PHP_INT_MAX;
        $profit=0;

        foreach($prices as $value)
        {
            if($value<$minPrice)
            {
                $minPrice = $value;
            }elseif($value-$minPrice>$profit)
            {
                $profit=$value-$minPrice;
            }
        }
        return $profit;
    }
```
### 10. 268. Missing Number

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.
Example 1:

Input: nums = [3,0,1]
Output: 2
```php
    function missingNumber($nums) {
        $n = count($nums);

        $arraySum = array_sum($nums);
        $mathSum = ($n*($n+1)/2);
        return $mathSum-$arraySum;
    }
```

### 11. 136. Single Number

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.
You must implement a solution with a linear runtime complexity and use only constant extra space.
Example 1:

Input: nums = [2,2,1]
Output: 1
```php
    function singleNumber($nums) {

        $newArray =[];

        foreach($nums as $value)
        {
            if(isset($newArray[$value]))
            {
                $newArray[$value]++;
            }else{
                $newArray[$value]=1;
            }
        }

        foreach($newArray as $key => $value)
        {
            if($newArray[$key] ==1)
            {
                return $key;
            }
        }
        
    }
```

### 12. 3452. Sum of Good Numbersr

Given an array of integers nums and an integer k, an element nums[i] is considered good if it is strictly greater than the elements at indices i - k and i + k (if those indices exist). If neither of these indices exists, nums[i] is still considered good.
Return the sum of all the good elements in the array.
Example 1:

Input: nums = [1,3,2,1,5,4], k = 2
Output: 12
Explanation:
The good numbers are nums[1] = 3, nums[4] = 5, and nums[5] = 4 because they are strictly greater than the numbers at indices i - k and i + k.
```php
    function sumOfGoodNumbers($nums, $k) {

       $sum = 0;
    $n = count($nums);

    for ($i = 0; $i < $n; $i++) {
        $isGood = true;

        // Check the element at index i - k, if it exists
        if ($i - $k >= 0 && $nums[$i] <= $nums[$i - $k]) {
            $isGood = false;
        }

        // Check the element at index i + k, if it exists
        if ($i + $k < $n && $nums[$i] <= $nums[$i + $k]) {
            $isGood = false;
        }

        // If the current element is good, add it to the sum
        if ($isGood) {
            $sum += $nums[$i];
        }
    }

    return $sum;
    }
```

### 13. 66. Plus One

You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.
Increment the large integer by one and return the resulting array of digits.
Example 1:
Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
Incrementing by one gives 123 + 1 = 124.
Thus, the result should be [1,2,4].

```php
    function plusOne($digits) {
        $n = count($digits);
    
    
    for ($i = $n - 1; $i >= 0; $i--) {
        if ($digits[$i] < 9) {
            $digits[$i]++;
            return $digits;
        }
        
        $digits[$i] = 0;
    }
    
    array_unshift($digits, 1);
    return $digits;
    }
```

### 14. 35. Search Insert Position

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
You must write an algorithm with O(log n) runtime complexity.
Example 1:
Input: nums = [1,3,5,6], target = 5
Output: 2

```php
   function searchInsert($nums, $target) {
        $n = count($nums);

        for($i=0;$i<$n;$i++)
        {
            if($nums[$i] == $target){
                return $i;
            }
        }

        for($j=0;$j<$n;$j++)
        {
            if($target<$nums[$j]){
                return $j;
            }
        }
        return $n;
    }
```

### 15. 27. Remove Element

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.
Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:
Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.

```php
  function removeElement(&$nums, $val) {
        $n = count($nums);
        $i=0;

        for($j=0;$j<$n;$j++)
        {
            if($nums[$j] !== $val)
            {
                $nums[$i] = $nums[$j];
                $i++;
            }
        }

        for($k=$i;$k<$n;$k++)
        {
            $nums[$k] = '_';
        }
        return $i;
    }
```



