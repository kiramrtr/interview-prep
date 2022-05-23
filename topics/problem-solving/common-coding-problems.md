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

### [Max Sub Array]

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
