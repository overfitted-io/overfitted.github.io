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
<span class="tag" id="LINKING">LINKING</span>
<span class="tag" id="SYSTEM-INFO">SYSTEM-INFO</span>


# Behaviour Tags
<span class="bhv-tag" id="na">N/A</span>

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
    [-13.542213439941406, -10.697185516357422, '<b><a href="/report/entry0@cbc200f66cbffbddf5df52f7c0da283a">entry0</a><br>@cbc200f66cbffbddf5df52f7c0da283a</b><br>', 'point { fill-color: #e0440e; }'],
[16.687074661254883, 15.439314842224121, '<b><a href="/report/entry0@009ea4ad185ccb9becba67b3b2163e8b">entry0</a><br>@009ea4ad185ccb9becba67b3b2163e8b</b><br>', 'null'],
[48.1448860168457, -8.476059913635254, '<b><a href="/report/entry0@8912a6bd1add3d8b86feb51a00252709">entry0</a><br>@8912a6bd1add3d8b86feb51a00252709</b><br>', 'null'],
[131.20819091796875, -63.49471664428711, '<b><a href="/report/entry0@bcba729302fe28f65deb2b102a06324a">entry0</a><br>@bcba729302fe28f65deb2b102a06324a</b><br>', 'null'],
[123.05802917480469, -30.351276397705078, '<b><a href="/report/entry0@7614e1bbe9b9fd3db78e405e68b1fab4">entry0</a><br>@7614e1bbe9b9fd3db78e405e68b1fab4</b><br>', 'null'],
[-13.230945587158203, -48.43284606933594, '<b><a href="/report/entry0@faca7110288761a0f664158c1f6c3986">entry0</a><br>@faca7110288761a0f664158c1f6c3986</b><br>', 'null'],
[153.35125732421875, -16.020151138305664, '<b><a href="/report/entry0@1c48774da6a3dd4bf3ea41716a332c61">entry0</a><br>@1c48774da6a3dd4bf3ea41716a332c61</b><br>', 'null'],
[49.756866455078125, -46.41298294067383, '<b><a href="/report/entry0@8a08237568bc7b1a4e9813b2af535d73">entry0</a><br>@8a08237568bc7b1a4e9813b2af535d73</b><br>', 'null'],
[162.05435180664062, -49.17234420776367, '<b><a href="/report/entry0@0fb0e1c162f9df68f5d89a2b2a71a217">entry0</a><br>@0fb0e1c162f9df68f5d89a2b2a71a217</b><br>', 'null'],
[17.92129135131836, -27.733383178710938, '<b><a href="/report/entry0@ea9c1e2eeb951a8e6185c6674c228f98">entry0</a><br>@ea9c1e2eeb951a8e6185c6674c228f98</b><br>', 'null'],
[19.144590377807617, -66.53132629394531, '<b><a href="/report/entry0@48bb9a03c360009e9463dfd5be4e0ca0">entry0</a><br>@48bb9a03c360009e9463dfd5be4e0ca0</b><br>', 'null'],

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
jne 0x40106b
push 0x1c
call fcn.0040112d
pop ecx
call fcn.00401a35
test eax, eax
jne 0x40107c
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
je 0x4010cb
movzx eax, word[ebp-0x2c]
jmp 0x4010ce
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