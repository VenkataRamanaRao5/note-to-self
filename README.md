## Javascript

- Javascript regex stores state if global flag is set. It will store the lastIndex, but does not reset on new string - stupid idiot.
`/https:\/\/enclose\.horse Day (\d+)\s* .* (?:PERFECT!|Excellent!|Great|okay) .* (\d+%)/g` return match for `"https://enclose.horse Day 53
🥈 Great 🥈 86%"` the first time, but returned null for the second time. I used ctrl F and both strings were exact same 🤦‍♀️. The solution is to avoid regex.exec(string), but use string.match(regex). That works as intended.  
https://dev.to/dvddpl/why-is-my-regex-working-intermittently-4f4g  
Then again, the idiot was me, because the global flag is to search for matches beyond the first match, while what I wanted was multiline matching. I could just replace the \s* part with \n. But I found [\s\S] that hacks around . not matching \n. Learnt something 👍.

- React navigation is interesting. Github copilot is interesting. It dives into the rusting implementation of a library to figure out an error. Claude sonnet 4.6 https://github.com/VenkataRamanaRao5/cbsa-app/pull/2 . Also, write workflows for build process, it makes life easier than running build everytime locally. 

## Python

- In google colab, I had three nested loops for building triplets for training GAT based on triplet loss (instead of building individual triplets, it was far faster and efficient to build batches and train those batches directly. I modified it later) and I wanted to monitor the progress of all the loops using tqdm. So, I used tqdm with position argument and leave = both false and true. But I kept running into the unplesantness of every progress bar appearing on a newline exactly as in this issue https://github.com/tqdm/tqdm/issues/1139. This issue is 9 years past deadline lol. Looking around, I was advised to use tqdm.auto.tqdm instead of tqdm.tqdm https://stackoverflow.com/questions/63908917/progress-bar-using-tqdm-prints-in-a-new-line-everytime-the-update-is-called-on. It worked like a charm. I unfortunately have modified the loops already to use batching, so I no longer have those loops to show an example output.

- We can create lists in python using `*` operator like so 
  ```
  >>> arr = [0] * 3
  >>> arr
  [0, 0, 0]
  ```
  Simple enough. But this can also be used to create multi-dimensional lists too.
  ```
  >>> matrix = [[0] * 3] * 3
  >>> matrix
  [[0, 0, 0], [0, 0, 0], [0, 0, 0]]
  ```
  Basically, `[x] * n` creates `n` copies of `x`. In the first case, `x` was `0`. In the second, `x` is `[0] * 3`. But there's a catch -- it is not `n` different copies of `x`, but instead, `n` copies of the same object `x`. So, whatever side effects you perform on one element, is also applied to every other element. But since `0` is an `int` and is immutable and also because we don't perform any modifications on `0` itself but only reassign `arr[i]`, it does not have any effect. But in case of `matrix`, see the output
  ```
  >>> matrix[0][0] = 2
  >>> matrix
  [[2, 0, 0], [2, 0, 0], [2, 0, 0]]
  ```
  That's beacuse all 3 rows are the same object
  ```
  >>> matrix[0] is matrix[1]
  True
  ```
  This effect can also be seen if instead of creating an integer list, if I had created a list of instances, calling a (side-effecting) method on one would have been equivalent to calling it on everything else. Or rather, there is only one object and all the indices would be reading that one single object which would have been updated.
  
  So, basically useless for creating multi-dimensional lists.

## LLMs

- Not exactly a note, but gemini pro made an actual typo. 
