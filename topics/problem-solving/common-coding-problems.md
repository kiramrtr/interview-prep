## Common Coding Problems

### [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

#### Naive solution:

```java
public boolean containsDuplicate(int[] nums) {
    for (int i = 0; i < nums.length - 1; i++) {
        for (int j = i + 1; j < nums.length; j++) {
            if (nums[i] == nums[j]) {
                return true;
            }
        }
    }
    return false;
}
```

#### By sorting:

```java
public boolean containsDuplicate(int[] nums) {
    Arrays.sort(nums);

    for (int i = 0; i < nums.length - 1; i++) {
        if (nums[i] == nums[i+1]) {
            return true;
        }
    }
    return false;
}
```

#### Using Set:

```java
public boolean containsDuplicate(int[] nums) {
    Set<Integer> numsSet = new HashSet<>();

    for (int i = 0; i < nums.length; i++) {
        if(numsSet.contains(nums[i])) {
            return true;
        } else {
            numsSet.add(nums[i]);
        }
    }
    return false;
}
```

### [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

#### Brute-force

#### Kadens algorithm

```java
public int maxSubArray(int[] nums) {
    int maxSeen = Integer.MIN_VALUE;
    int currentMax = 0;

    for (int i = 0; i < nums.length; i++) {
        currentMax = currentMax + nums[i];

        if (currentMax > maxSeen) {
            maxSeen = currentMax;
        }

        if (currentMax < 0) {
            currentMax = 0;
        }
    }

    return maxSeen;
}
```

### [Merge Sorted Array (In-place)](https://leetcode.com/problems/merge-sorted-array/)

> _Intuition:_
> As the result is going to be increasing order, traversing both the arrays from the end and placing the largest on from the end of the list.

```java
public static void merge(int[] nums1, int m, int[] nums2, int n) {
    int i = m - 1;
    int j = n - 1;
    int idx = (m + n) - 1;

    while (i >= 0 && j >= 0) {
        if (nums1[i] > nums2[j]) {
            nums1[idx--] = nums1[i--];
        } else {
            nums1[idx--] = nums2[j--];
        }
    }

    while (j >= 0) {
        nums1[idx--] = nums2[j--];
    }
}
```

### [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

```java
public int maxProfit(int[] prices) {
    int minPrice = Integer.MAX_VALUE;
    int maxProfit = 0;

    for (int i = 0; i < prices.length; i++) {
        if (prices[i] < minPrice) {
            minPrice = prices[i];
        } else if (prices[i] - minPrice > maxProfit) {
            maxProfit = prices[i] - minPrice;
        }
    }

    return maxProfit;
}
```

### [Two Sum](https://leetcode.com/problems/two-sum/)

```java
public int[] twoSum(int[] nums, int target) {
    for (int i = 0; i < nums.length - 1; i++) {
        for (int j = i+1; j < nums.length; j++) {
            if (nums[i] + nums[j] == target) {
                return new int[] { i, j };
            }
        }
    }

    return new int[0];
}
```

### [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

```java
public boolean isPalindrome(int x) {
    if (x < 0) { return false; }

    int n = x;
    int reverse = 0;

    while (n != 0) {
        int remainder = n % 10;
        n = n / 10;

        reverse = reverse * 10 + remainder;
    }

    if (x == reverse) { return true; }

    return false;
}
```

### [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

```java
public int removeDuplicates(int[] nums) {
    if (nums.length == 0 || nums.length == 1) {
        return nums.length;
    }

    int i = 0;
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }

    return i + 1;
}
```

### [Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

```java
public int findMaxConsecutiveOnes(int[] nums) {
    int maxSeen = 0, currentMax = 0;

    for (int i = 0; i < nums.length; i++) {
        if (nums[i] == 1) {
            currentMax += 1;
            maxSeen = Math.max(currentMax, maxSeen);
        } else {
            currentMax = 0;
        }
    }

    return maxSeen;
}
```

### [Consecutive Characters](https://leetcode.com/problems/consecutive-characters/)

```java
public int maxPower(String s) {
    int max = 0, currentCount = 0;
    char prevChar = ' ';

    for (int i = 0; i < s.length(); i++) {
        char currentChar = s.charAt(i);

        if (prevChar == currentChar) {
            currentCount++;
        } else {
            prevChar = currentChar;
            currentCount = 1;
        }
        max = Math.max(max, currentCount);
    }
    return max;
}
```
