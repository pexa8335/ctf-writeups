
#Medium
# Description 📝

Sometimes you need to handle process data outside of a file. 🗂️ Can you find a way to keep the output from this program and search for the flag? 🚩 Connect to `jupiter.challenges.picoctf.org 14291`.

---

## Write up. ✍️

When using hints, you would see a pipe.html file, this is a trap. 🪤
The demand is "keep the output from this program" so just using netcad to connect to `jupiter.challenges.picoctf.org 14291` and find the picoCTF flag.

But, you won't need to search for a single line, we have grep. 🔍

The syntax of the flag is always `picoCTF` so we will grep the phrase `picoCTF` from the output.

```
nc jupiter.challenges.picoctf.org 14291 | grep picoCTF
```

Successfully: picoCTF{digital_plumb3r_ea8bfec7} ✅
