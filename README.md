# chicken-invaders-reverse-engineering
Reverse engineering and runtime memory modification of a legacy game using x32dbg — IE3042 Secure Software Systems assignment.
# Reverse Engineering and Runtime Modification of Chicken Invaders Using x32dbg

**Course:** IE3042 – Secure Software Systems  
**Student:** Sathursha Ravichandran  
**Year 3, Semester 1**

## Overview
This project demonstrates reverse engineering and runtime memory modification 
of a legacy game (Chicken Invaders) using the x32dbg debugger. The goal was to 
locate the assembly instruction responsible for decreasing the player's life 
value and modify it at runtime to disable the damage system.

## Environment & Tools
- **Virtual Machine:** Oracle VM VirtualBox
- **Guest OS:** Windows 11
- **Debugger:** x32dbg

## Summary of Work
1. Set up an isolated virtual environment for safe testing
2. Attached x32dbg to the running Chicken Invaders process
3. Used breakpoints and runtime inspection to trace the player's life value in memory
4. Identified the key instruction:  
   `dec dword ptr ds:[edi+E4]`
5. Patched the instruction with `NOP` (No Operation) to disable the life-decrement logic
6. Verified the modification — player life remained constant after being hit

## Security Findings
The exercise exposed several weaknesses typical of legacy applications:
- No anti-debugging protection
- No memory protection
- No runtime integrity checks
- Critical values (like player life) stored in plain, predictable memory locations

### Recommended Mitigations
- Code obfuscation
- Anti-debugging techniques
- Runtime integrity verification
- Encrypted memory handling
- Secure coding practices

## Files in this Repository
- `SSS_Assignment_Report.pdf` — Full assignment report with analysis and screenshots
- `demo-video.mp4` (or link below) — Video walkthrough of the reverse engineering and patching process

## Demo Video
[Watch the demo video](https://mysliit-my.sharepoint.com/:v:/g/personal/it23642300_my_sliit_lk/IQAgceIq3J3lS4wv43PESGkHAfLvDb7SsQPImp7kjjimbfU?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=lEMkj8)

## Disclaimer
This project was conducted strictly for **educational purposes** in a controlled, 
isolated virtual environment as part of a university coursework assignment on 
software security concepts.
