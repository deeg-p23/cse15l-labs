### Part 1

**Failure-Inducing Input for jUnit Test**
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 5, 4, 3, 2, 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1, 2, 3, 4, 5 }, input1);
}
```

**Pass-Inducing Input for jUnit Test**
```
@Test 
public void testReverseInPlace() {
    int[] input1 = { 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1 }, input1);
}
```

**Symptom Shown by Running Tests**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/5fcaa1c2-b231-4ada-8e91-6447d81e3d98)

**Bug Fix for reverseInPlace(int[] arr)**

_Before:_

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
        arr[i] = arr[arr.length - i - 1];
    }
}
```

_After:_

```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length/2; i += 1) {
        int tempInt = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = tempInt;
    }
}
```

---
### Part 2

**-iname #1**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/4164fc58-34ca-4792-97f7-e65e9a9fb18a)

find -iname will show you all the files from the working directory onwards based on the relative keywords you gave it for the file names. Placing asterisks on one side of a phrase given will assume the rest of it is unknown, and it's up for the command to output files that have relatively matching names.

**-iname #2**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/d02482f1-1238-4554-8a09-bdaf1cc3f172)

find -iname can also be used with question marks instead of asterisks, which are used to denote an exact number of unknown characters in the file. In the example above, three "?"s after "preface" doesn't show anything, but four of them show up "preface.txt", because it takes four characters to get ".txt".

**-type #1**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/bc78b579-55dd-419d-a2ad-d7fdb0b36315)

find -type will find you all files from the working directory onwards based on the character you give it corresponding to a type to filter through. In the above example, 'd' will find and give all directories that exist within the working directory.

**-type #2**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/ff3d9e9d-7d34-4f76-865f-a8bc66293000)

find -type has various other character arguments you can use as filters. In the above example, 'f' corresponds to all file types, which is why it gives various .txt files (the actual output was much larger, but the image is trimmed for content-height purposes).

**-maxdepth #1**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/6bbb8c2f-cf16-4a77-a4f5-5e8a41bf565f)

find -maxdepth will find you all entries from the working directory onwards up until the value of directory depths given. In the above example, 1 is given as the argument, so only the 0th layer, which is the current directory, and the 1st layer, the two directories under it, are returned. 

**-maxdepth #2**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/95cbfb38-3a9d-4e6e-831a-415ae3e41e1f)

find -maxdepth can continue having larger numbers, meaning higher depths, and therefore larger quantities of entries returned as a result. In the above example, 2 is given as the argument, so the current directory, the two directories under it, and all files under both directories are returned (once again, the result is much larger than shown).

**-size #1**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/573628db-295b-43ac-92a4-c9ed28c1299b)

find -size will find you all files (not directories) that have sizes matching the argument given. In the above example, '+' represents greater than the following number, which is 100 of 'k''s, which represent kilobytes. Therefore, the files returned are all greater than 100kb in size.

**-size #2**

![image](https://github.com/deeg-p23/cse15l-labs/assets/133953132/03d32fd3-0073-4f07-b3bb-10ddf32540f6)

find -size can use various operators (greater or less than), integer values, and byte sizes (bytes, kilobytes, megabytes, gigabytes). The above example uses "+200k" to show files which are greater than 200kb in size, returning even fewer files than the previous command.
