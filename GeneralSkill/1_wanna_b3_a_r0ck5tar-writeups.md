#Medium 🎼
## Description

I wrote you another [song](https://jupiter.challenges.picoctf.org/static/b99c57e4274172bf3c93534b6d59632d/lyrics.txt). Put the flag in the picoCTF{} flag format. 🚩

---

## Write up

This is the Rockstar language, not just a song. 🎸

There are 2 ways to solve this:
1. "Understand the Language Specification" (i.e., learn Rockstar language rules) 🤔

2. Or use a **Python transpiler** (a program that converts Rockstar code into Python) 🐍

I will use way 2 to solve this problem.

To convert Rockstar code to Python, use the Python transpiler tool: `rockstar-py`.

```bash
rockstar-py --output rockstar.py -i lyrics.txt
```
Understand the syntax:
1. Put the output code into rockstar.py.
2. The input is from the lyrics.txt file. 📝

---
If you have not downloaded rockstar-py before, use the following commands:

```bash
sudo apt update
sudo apt install pipx
pipx ensurepath
pipx install rockstar-py
source ~/.bashrc
```

---
```python
if the_music == a_guitar:
    print("Keep on rocking!")
    the_rhythm = int(input())
    if the_rhythm - Music == 0:
        Tommy = 66
        print(Tommy)
        Music = 79
        Jamming = 78
        print(Music)
        print(Jamming)
        Tommy = 74
        print(Tommy)
#        They are dazzled audiences
        print("it!")
        Rock = 86
        print("it!")
        Tommy = 73
        print("it!")
        print("Bring on the rock!")
    else: print("That ain't it, Chief")
```
>In Rockstar language, `it` will store the last value that was assigned. For instance, if there is an assignment Tommy = 74, it = 74.

Look at the section code, we see that in the `if` section, it has a series of numbers 66, 79, 78, 74, 74, 86, 73. The `else` condition throws a failure message, but I tried to enter 66, 79, 78, 74, 86, 73 and submitted but it was false -> convert to ASCII instead. ⌨️

BONJJVI -> still not the flag. 🙅

The problem is: They are dazzled audiences -> **This is the key point!** 🔑

- They is an **alias** for it.
- This syntax looks like a Poetic Number Literal Assignment for it.
- dazzled -> 7 letters -> digit 7
- audiences -> 9 letters -> digit 9
- So this line performs the assignment: it = 79.

=> 66 79 78 74 79 86 73
=> BONJOVI - The flag captured successfully. 🎉

