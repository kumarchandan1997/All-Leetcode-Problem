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

### 1. 242. Valid Anagram

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