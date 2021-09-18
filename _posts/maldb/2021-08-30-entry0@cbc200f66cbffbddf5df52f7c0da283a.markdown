---
layout: post
title:  "entry0 @ cbc200f66cbffbddf5df52f7c0da283a"
date:   2021-09-10 15:52:19 +0300
categories: report
index: false
---

# Generic Information
- **Function:** entry0
- **Origin (md5):** cbc200f66cbffbddf5df52f7c0da283a
- **VirusTotal:** [virustotal.com/gui/file/cbc200f66cbffbddf5df52f7c0da283a][virustotal_ref]

# Code Tags
<span class="tag" id="PROCESS">PROCESS</span>
<span class="tag" id="LINKING">LINKING</span>
<span class="tag" id="SYSTEM-INFO">SYSTEM-INFO</span>


# Estimated Behaviour
<ul><li class="bhv-desc" id="na">Not Available :(</li></ul>

# Similar Functions
<script type="text/javascript" src="https://www.gstatic.com/charts/loader.js"></script>
<script type="text/javascript">

    google.charts.load('current', {'packages':['corechart']});
    google.charts.setOnLoadCallback(drawChart);

    function drawChart() {
    var data = new google.visualization.DataTable();
        data.addColumn('number', 'X');
        data.addColumn('number', 'Y');
        data.addColumn({type: 'string', role: 'tooltip', 'p': {'html': true}});
        data.addColumn({'type': 'string', 'role': 'style'});
        
        data.addRows([
    [72.05947875976562, 61.85666275024414, '<b><a href="/report/entry0@cbc200f66cbffbddf5df52f7c0da283a">entry0</a><br>@cbc200f66cbffbddf5df52f7c0da283a</b><br>', 'point { fill-color: #e0440e; }'],
[-246.01885986328125, 211.59854125976562, '<b><a href="/report/entry0@4e8d6f73c8261716f687f8d06429ef4d">entry0</a><br>@4e8d6f73c8261716f687f8d06429ef4d</b><br>', 'null'],
[-314.9240417480469, -2.935127019882202, '<b><a href="/report/entry0@140d3779c34998b2115004c062b02ca8">entry0</a><br>@140d3779c34998b2115004c062b02ca8</b><br>', 'null'],
[-191.83209228515625, -184.38482666015625, '<b><a href="/report/entry0@48bb9a03c360009e9463dfd5be4e0ca0">entry0</a><br>@48bb9a03c360009e9463dfd5be4e0ca0</b><br>', 'null'],
[40.191436767578125, -444.5487976074219, '<b><a href="/report/entry0@009ea4ad185ccb9becba67b3b2163e8b">entry0</a><br>@009ea4ad185ccb9becba67b3b2163e8b</b><br>', 'null'],
[158.9312286376953, 261.5223388671875, '<b><a href="/report/entry0@8a08237568bc7b1a4e9813b2af535d73">entry0</a><br>@8a08237568bc7b1a4e9813b2af535d73</b><br>', 'null'],
[-113.24178314208984, 39.01731872558594, '<b><a href="/report/entry0@7dd153bad1771b9e8d5266a341ebf949">entry0</a><br>@7dd153bad1771b9e8d5266a341ebf949</b><br>', 'null'],
[277.8799743652344, 70.1379165649414, '<b><a href="/report/entry0@faca7110288761a0f664158c1f6c3986">entry0</a><br>@faca7110288761a0f664158c1f6c3986</b><br>', 'null'],
[2.5933010578155518, -137.5301971435547, '<b><a href="/report/entry0@a2475448bf4050c1583e1970984a4d00">entry0</a><br>@a2475448bf4050c1583e1970984a4d00</b><br>', 'null'],
[202.57177734375, -135.8057861328125, '<b><a href="/report/entry0@3e981d1767f44f5fe2446a49ffe52f4e">entry0</a><br>@3e981d1767f44f5fe2446a49ffe52f4e</b><br>', 'null'],
[-45.905052185058594, 255.71408081054688, '<b><a href="/report/entry0@ea9c1e2eeb951a8e6185c6674c228f98">entry0</a><br>@ea9c1e2eeb951a8e6185c6674c228f98</b><br>', 'null'],

        ]);

    var options = {
        title: 'Similarity Plot',
        legend: 'none',
        colors: ['#dedbd9', '#e6693e', '#ec8f6e', '#f3b49f', '#f6c7b6'],
        tooltip: {isHtml: true, trigger: 'both'},
        explorer: {
        actions: ["dragToZoom", "rightClickToReset"],
        },
        chartArea: {
        width: '80%',
        height: '80%'
        },
        width: '100%',
        height: '100%'
    };

    var chart = new google.visualization.ScatterChart(document.getElementById('chart_div'));

    chart.draw(data, options);
    }
    
</script>


<div id="chart_div" style="width: 100%px; height: 100%;"></div>

# Disassembled Code
{% highlight nasm %}

push ebp
mov ebp, esp
push 0xffffffffffffffff
push 0x40b158
push 0x401dd0
mov eax, dword
push eax
mov dword
sub esp, 0x58
push ebx
push esi
push edi
mov dword[ebp-0x18], esp
call dword[sym.imp.KERNEL32.dll_GetVersion]
xor edx, edx
mov dl, ah
mov dword[0x445a6a4], edx
mov ecx, eax
and ecx, 0xff
mov dword[0x445a6a0], ecx
shl ecx, 8
add ecx, edx
mov dword[0x445a69c], ecx
shr eax, 0x10
mov dword[0x445a698], eax
push 1
call fcn.00401c78
pop ecx
test eax, eax
jne off.b107
push 0x1c
call fcn.0040112d
pop ecx
call fcn.00401a35
test eax, eax
jne off.b124
push 0x10
call fcn.0040112d
pop ecx
xor esi, esi
mov dword[ebp-4], esi
call fcn.00401879
call dword[sym.imp.KERNEL32.dll_GetCommandLineA]
mov dword[0x445ad58], eax
call fcn.00401747
mov dword[0x445a688], eax
call fcn.004014fa
call fcn.00401441
call fcn.00401151
mov dword[ebp-0x30], esi
lea eax, [ebp-0x5c]
push eax
call dword[sym.imp.KERNEL32.dll_GetStartupInfoA]
call fcn.004013e9
mov dword[ebp-0x64], eax
test byte[ebp-0x30], 1
je off.b203
movzx eax, word[ebp-0x2c]
jmp off.b206
push 0xa
pop eax
push eax
push dword[ebp-0x64]
push esi
push esi
call dword[sym.imp.KERNEL32.dll_GetModuleHandleA]
push eax
call main
mov dword[ebp-0x60], eax
push eax
call fcn.0040117e
mov eax, dword[ebp-0x14]
mov ecx, dword[eax]
mov ecx, dword[ecx]
mov dword[ebp-0x68], ecx
push eax
push ecx
call fcn.00401271
pop ecx
pop ecx
ret

{% endhighlight %}

[virustotal_ref]: https://www.virustotal.com/gui/file/cbc200f66cbffbddf5df52f7c0da283a