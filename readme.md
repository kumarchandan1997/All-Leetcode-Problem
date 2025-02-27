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