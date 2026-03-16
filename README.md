## Javascript

- Javascript regex stores state if global flag is set. It will store the lastIndex, but does not reset on new string - stupid idiot.
`/https:\/\/enclose\.horse Day (\d+)\s* .* (?:PERFECT!|Excellent!|Great|okay) .* (\d+%)/g` return match for `"https://enclose.horse Day 53
🥈 Great 🥈 86%"` the first time, but returned null for the second time. I used ctrl F and both strings were exact same 🤦‍♀️. The solution is to avoid regex.exec(string), but use string.match(regex). That works as intended.  
https://dev.to/dvddpl/why-is-my-regex-working-intermittently-4f4g  
Then again, the idiot was me, because the global flag is to search for matches beyond the first match, while what I wanted was multiline matching. I could just replace the \s* part with \n. But I found [\s\S] that hacks around . not matching \n. Learnt something 👍.

- React navigation is interesting. Github copilot is interesting. It dives into the rusting implementation of a library to figure out an error. Claude sonnet 4.6 https://github.com/VenkataRamanaRao5/cbsa-app/pull/2 . Also, write workflows for build process, it makes life easier than running build everytime locally. 

## Python

- In google colab, I had three nested loops for building triplets for training GAT based on triplet loss (instead of building individual triplets, it was far faster and efficient to build batches and train those batches directly. I modified it later) and I wanted to monitor the progress of all the loops using tqdm. So, I used tqdm with position argument and leave = both false and true. But I kept running into the unplesantness of every progress bar appearing on a newline exactly as in this issue https://github.com/tqdm/tqdm/issues/1139. This issue is 9 years past deadline lol. Looking around, I was advised to use tqdm.auto.tqdm instead of tqdm.tqdm https://stackoverflow.com/questions/63908917/progress-bar-using-tqdm-prints-in-a-new-line-everytime-the-update-is-called-on. It worked like a charm. I unfortunately have modified the loops already to use batching, so I no longer have those loops to show an example output.

## LLMs

- Not exactly a note, but gemini pro made an actual typo. 
