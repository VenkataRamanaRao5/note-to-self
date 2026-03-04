## Javascript

- Javascript regex stores state if global flag is set. It will store the lastIndex, but does not reset on new string - stupid idiot.
`/https:\/\/enclose\.horse Day (\d+)\s* .* (?:PERFECT!|Excellent!|Great|okay) .* (\d+%)/g` return match for `"https://enclose.horse Day 53
🥈 Great 🥈 86%"` the first time, but returned null for the second time. I used ctrl F and both strings were exact same 🤦‍♀️. The solution is to avoid regex.exec(string), but use string.match(regex). That works as intended.  
https://dev.to/dvddpl/why-is-my-regex-working-intermittently-4f4g  
Then again, the idiot was me, because the global flag is to search for matches beyond the first match, while what I wanted was multiline matching. I could just replace the \s* part with \n. But I found [\s\S] that hacks around . not matching \n. Learnt something 👍.

- React navigation is interesting. Github copilot is interesting. It dives into the rusting implementation of a library to figure out an error. Claude sonnet 4.6 https://github.com/VenkataRamanaRao5/cbsa-app/pull/2 . Also, write workflows for build process, it makes life easier than running build everytime locally. 
