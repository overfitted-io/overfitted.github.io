---
layout: post
title:  "entry0 @ fac4f0be03ac37bd8be7ef737cdcee10"
date:   2021-08-30 15:52:19 +0300
categories: report
index: false
---

# Generic Information
- **Function:** entry0
- **Origin (md5):** fac4f0be03ac37bd8be7ef737cdcee10
- **VirusTotal:** [virustotal.com/gui/file/fac4f0be03ac37bd8be7ef737cdcee10][virustotal_ref]

# Code Tags
<span class="tag" id="LINKING">LINKING</span>
<span class="tag" id="SYSTEM-INFO">SYSTEM-INFO</span>


# Similar Functions

1. [entry0][similar_1_ref] (sim.: 0.9511623545097517)
2. [entry0][similar_2_ref] (sim.: 0.9202926505097098)
3. [entry0][similar_3_ref] (sim.: 0.9112228138517283)
4. [entry0][similar_4_ref] (sim.: 0.904592872547257)
5. [entry0][similar_5_ref] (sim.: 0.9045396729627216)


# Disassembled Code

{% highlight nasm %}
push 0x60
push 0x430f00
call fcn.00411e98
mov edi,0x94
mov eax,edi
call fcn.0040e0a0
mov dword[ebp-0x18],esp
mov esi,esp
mov dword[esi],edi
push esi
call dword[sym.imp.KERNEL32.dll_GetVersionExA]
mov ecx,dword[esi+0x10]
mov dword[0x461ffc],ecx
mov eax,dword[esi+4]
mov dword[0x462008],eax
mov edx,dword[esi+8]
mov dword[0x46200c],edx
mov esi,dword[esi+0xc]
and esi,0x7fff
mov dword[0x462000],esi
cmp ecx,2
je 0x40ea5f
or esi,0x8000
mov dword[0x462000],esi
shl eax,8
add eax,edx
mov dword[0x462004],eax
xor esi,esi
push esi
mov edi,dword[sym.imp.KERNEL32.dll_GetModuleHandleA]
call edi
cmp word[eax],0x5a4d
jne 0x40ea9a
mov ecx,dword[eax+0x3c]
add ecx,eax
cmp dword[ecx],0x4550
jne 0x40ea9a
movzx eax,word[ecx+0x18]
cmp eax,0x10b
je 0x40eab2
cmp eax,0x20b
je 0x40ea9f
mov dword[ebp-0x1c],esi
jmp 0x40eac6
cmp dword[ecx+0x84],0xe
jbe 0x40ea9a
xor eax,eax
cmp dword[ecx+0xf8],esi
jmp 0x40eac0
cmp dword[ecx+0x74],0xe
jbe 0x40ea9a
xor eax,eax
cmp dword[ecx+0xe8],esi
setne al
mov dword[ebp-0x1c],eax
push 1
call fcn.00412688
pop ecx
test eax,eax
jne 0x40eada
push 0x1c
call fcn.0040e9db
pop ecx
call fcn.004140b8
test eax,eax
jne 0x40eaeb
push 0x10
call fcn.0040e9db
pop ecx
call fcn.0041425c
mov dword[ebp-4],esi
call fcn.00415464
test eax,eax
jge 0x40eb04
push 0x1b
call fcn.0040e9b6
pop ecx
call dword[sym.imp.KERNEL32.dll_GetCommandLineA]
mov dword[0x463920],eax
call fcn.00415342
mov dword[0x462040],eax
call fcn.004152a0
test eax,eax
jge 0x40eb2a
push 8
call fcn.0040e9b6
pop ecx
call fcn.0041506d
test eax,eax
jge 0x40eb3b
push 9
call fcn.0040e9b6
pop ecx
push 1
call fcn.0040e6d7
pop ecx
mov dword[ebp-0x28],eax
cmp eax,esi
je 0x40eb51
push eax
call fcn.0040e9b6
pop ecx
mov dword[ebp-0x44],esi
lea eax,[ebp-0x70]
push eax
call dword[sym.imp.KERNEL32.dll_GetStartupInfoA]
call fcn.00415010
mov dword[ebp-0x20],eax
test byte[ebp-0x44],1
je 0x40eb72
movzx eax,word[ebp-0x40]
jmp 0x40eb75
push 0xa
pop eax
push eax
push dword[ebp-0x20]
push esi
push esi
call edi
push eax
call fcn.0041d71e
mov edi,eax
mov dword[ebp-0x2c],edi
cmp dword[ebp-0x1c],esi
jne 0x40eb93
push edi
call fcn.0040e804
call fcn.0040e826
jmp 0x40ebc5
or dword[ebp-4],0xffffffff
mov eax,edi
lea esp,[ebp-0x7c]
call fcn.00411ed3
ret 
{% endhighlight %}


[similar_1_ref]: /report/entry0@59aef7c08025d70f84c85db2092fc99e
[similar_2_ref]: /report/entry0@1123b7aa5760238fe93045e585b8234c
[similar_3_ref]: /report/entry0@de21a548b66aa6c0b17491b6a31e14fa
[similar_4_ref]: /report/entry0@0aa2d73a5300dff2412388945614b507
[similar_5_ref]: /report/entry0@6c5b0418e4a4c57d99cda47d2717045d
[virustotal_ref]: https://www.virustotal.com/gui/file/fac4f0be03ac37bd8be7ef737cdcee10