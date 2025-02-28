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

