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

# Using Set:

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
