
reverse -> find addr cmp two final string -> hook it get and modify.
```shell
 gdb impossible_password.bin                                                                                                    130 ↵
GNU gdb (Ubuntu 12.1-0ubuntu1~22.04.2) 12.1
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
GEF for linux ready, type `gef' to start, `gef config' to configure
93 commands loaded and 5 functions added for GDB 12.1 in 0.00ms using Python engine 3.10
Reading symbols from impossible_password.bin...
(No debugging symbols found in impossible_password.bin)
gef➤  info func
All defined functions:

Non-debugging symbols:
0x00000000004005f0  putchar@plt
0x0000000000400600  printf@plt
0x0000000000400610  __libc_start_main@plt
0x0000000000400620  srand@plt
0x0000000000400630  strcmp@plt
0x0000000000400640  __gmon_start__@plt
0x0000000000400650  time@plt
0x0000000000400660  malloc@plt
0x0000000000400670  __isoc99_scanf@plt
0x0000000000400680  exit@plt
0x0000000000400690  rand@plt
gef➤  break *0x0400961
Breakpoint 1 at 0x400961
gef➤  r
Starting program: /mnt/c/share/code/ctf/hackthebox/Impossible Password/impossible_password.bin
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
* SuperSeKretKey
[SuperSeKretKey]
** abc

Breakpoint 1, 0x0000000000400961 in ?? ()
[ Legend: Modified register | Code | Heap | Stack | String ]
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── registers ────
$rax   : 0x00007fffffffd8c0  →  0x4b65537200636261 ("abc"?)
$rbx   : 0x0
$rcx   : 0x5e
$rdx   : 0x0000000000602ac0  →  "ZGMYQ*B-C/BUBJ{NE]f3"
$rsp   : 0x00007fffffffd890  →  0x00007fffffffd9f8  →  0x00007fffffffdcba  →  "/mnt/c/share/code/ctf/hackthebox/Impossible Passwo[...]"
$rbp   : 0x00007fffffffd8e0  →  0x0000000000000001
$rsi   : 0x0000000000602ac0  →  "ZGMYQ*B-C/BUBJ{NE]f3"
$rdi   : 0x00007fffffffd8c0  →  0x4b65537200636261 ("abc"?)
$rip   : 0x0000000000400961  →   call 0x400630 <strcmp@plt>
$r8    : 0x0
$r9    : 0x00007ffff7fa6280  →  0x0000000000000008
$r10   : 0x00007ffff7d950f0  →  0x000f0012000027bc
$r11   : 0x00007ffff7dd2760  →  <rand+0000> endbr64
$r12   : 0x00007fffffffd9f8  →  0x00007fffffffdcba  →  "/mnt/c/share/code/ctf/hackthebox/Impossible Passwo[...]"
$r13   : 0x000000000040085d  →   push rbp
$r14   : 0x0
$r15   : 0x00007ffff7ffd040  →  0x00007ffff7ffe2e0  →  0x0000000000000000
$eflags: [zero carry PARITY adjust sign trap INTERRUPT direction overflow resume virtualx86 identification]
$cs: 0x33 $ss: 0x2b $ds: 0x00 $es: 0x00 $fs: 0x00 $gs: 0x00
0x00007fffffffd890│+0x0000: 0x00007fffffffd9f8  →  0x00007fffffffdcba  →  "/mnt/c/share/code/ctf/hackthebox/Impossible Passwo[...]"      ← $rsp
0x00007fffffffd898│+0x0008: 0x0000000100000000
0x00007fffffffd8a0│+0x0010: "A]Kr=9k0=0o0;k1?k81t"
0x00007fffffffd8a8│+0x0018: "=0o0;k1?k81t"
0x00007fffffffd8b0│+0x0020: 0x000000007431386b ("k81t"?)
0x00007fffffffd8b8│+0x0028: 0x0000000000000000
0x00007fffffffd8c0│+0x0030: 0x4b65537200636261 ("abc"?)  ← $rax, $rdi
0x00007fffffffd8c8│+0x0038: 0x000079654b746572 ("retKey"?)
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── code:x86:64 ────
     0x400957                  lea    rax, [rbp-0x20]
     0x40095b                  mov    rsi, rdx
     0x40095e                  mov    rdi, rax
 →   0x400961                  call   0x400630 <strcmp@plt>
   ↳    0x400630 <strcmp@plt+0000> jmp    QWORD PTR [rip+0x200a02]        # 0x601038 <strcmp@got.plt>
        0x400636 <strcmp@plt+0006> push   0x4
        0x40063b <strcmp@plt+000b> jmp    0x4005e0
        0x400640 <__gmon_start__@plt+0000> jmp    QWORD PTR [rip+0x2009fa]        # 0x601040 <__gmon_start__@got.plt>
        0x400646 <__gmon_start__@plt+0006> push   0x5
        0x40064b <__gmon_start__@plt+000b> jmp    0x4005e0
───────────────────────────────────────────────────────────────────────────────────────────────────────────────── arguments (guessed) ────
strcmp@plt (
   $rdi = 0x00007fffffffd8c0 → 0x4b65537200636261 ("abc"?),
   $rsi = 0x0000000000602ac0 → "ZGMYQ*B-C/BUBJ{NE]f3",
   $rdx = 0x0000000000602ac0 → "ZGMYQ*B-C/BUBJ{NE]f3"
)
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── threads ────
[#0] Id 1, Name: "impossible_pass", stopped 0x400961 in ?? (), reason: BREAKPOINT
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── trace ────
[#0] 0x400961 → call 0x400630 <strcmp@plt>
[#1] 0x7ffff7db5d90 → __libc_start_call_main(main=0x40085d, argc=0x1, argv=0x7fffffffd9f8)
[#2] 0x7ffff7db5e40 → __libc_start_main_impl(main=0x40085d, argc=0x1, argv=0x7fffffffd9f8, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fffffffd9e8)
[#3] 0x4006c9 → hlt
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
gef➤  x/s $rsi
0x602ac0:       "ZGMYQ*B-C/BUBJ{NE]f3"
gef➤  x/s $rdi
0x7fffffffd8c0: "abc"
gef➤  set $rdi="ZGMYQ*B-C/BUBJ{NE]f3"
gef➤  c
Continuing.
HTB{40b949f92b86b18}
[Inferior 1 (process 46424) exited with code 012]

```