# Rev Bin!
### Time to Capture!
Task-2 for PClub Y21 Secretary Recruitment

## Description
> You are provided with a binary file [here](https://drive.google.com/file/d/13gbVMtm2vH40XCqEyT1WBrPhgSlRkgz0/view?usp=sharing) 🔗
A password is hidden in some form in this binary file. Your task is to reverse engineer the binary to get the password.  
Write a detailed writeup (containing the password) as a markdown file, push any associated code into a private github repository, make it public ONLY after the deadline!  
You may use any programming language, binary exploitation tool to solve this task.

## Approach
> We are provided with a binary file and we want to reverse engineer it to get the password. So, Ghidra can be used here for the analysis of the file.  

## Analysis with Ghidra
> We first create a new ghidra project and add the given binary file to it. And then open it in the Code Browser for its analysis. There we get to see all of the assembly code.  
On opening the 'Defined Strings' from Window option, one can easily find the string "Access Granted!". And also where it is present in the assembly code.[Screenshot 1](./Assets/Screenshot%20(38).png) Then, opening the decompiled code, we get to see the main function, at the end of which, is a condition, checking for `iVar1` to be `1`, to print "Access Granted!". Where `iVar1` is `checkpassword(local_33)` ![Screenshot 2](./Assets/Screenshot%20(39).png)
The function `checkpassword` also returns the bool value of `checkRes(in_stack_ffffff74) == 1`. ![Screenshot 3](./Assets/Screenshot%20(40).png) Now, `checkRes` return `1`, when `0x1d < local_10`, ![Screenshot 4](./Assets/Screenshot%20(41).png)  where `local_10` is `0`. That means, it just checks `0x1d < 0`.