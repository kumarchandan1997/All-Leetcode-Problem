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
