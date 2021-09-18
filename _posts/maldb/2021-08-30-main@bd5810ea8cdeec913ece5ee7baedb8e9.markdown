---
layout: post
title:  "main @ bd5810ea8cdeec913ece5ee7baedb8e9"
date:   2021-09-10 15:52:19 +0300
categories: report
index: false
---

# Generic Information
- **Function:** main
- **Origin (md5):** bd5810ea8cdeec913ece5ee7baedb8e9
- **VirusTotal:** [virustotal.com/gui/file/bd5810ea8cdeec913ece5ee7baedb8e9][virustotal_ref]

# Code Tags
<span class="tag" id="LINKING">LINKING</span>


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
    [14.337735176086426, 6.3173980712890625, '<b><a href="/report/main@bd5810ea8cdeec913ece5ee7baedb8e9">main</a><br>@bd5810ea8cdeec913ece5ee7baedb8e9</b><br>', 'point { fill-color: #e0440e; }'],
[11.522785186767578, -46.66078186035156, '<b><a href="/report/main@e9c6b3bcaa2edc455cb26f1e0f4a513a">main</a><br>@e9c6b3bcaa2edc455cb26f1e0f4a513a</b><br>', 'null'],
[-52.25442886352539, -30.28835678100586, '<b><a href="/report/main@31d828bf241be93b3ffe89cf3c313d44">main</a><br>@31d828bf241be93b3ffe89cf3c313d44</b><br>', 'null'],
[74.79669952392578, 25.925067901611328, '<b><a href="/report/main@41d541db4a17e11df1b616218be77825">main</a><br>@41d541db4a17e11df1b616218be77825</b><br>', 'null'],
[76.67770385742188, -37.07676315307617, '<b><a href="/report/main@6312517583453b51c66fd5c06a181092">main</a><br>@6312517583453b51c66fd5c06a181092</b><br>', 'null'],
[-28.43058204650879, -92.53621673583984, '<b><a href="/report/main@773e84b03dfb92871dd754ab3c01c180">main</a><br>@773e84b03dfb92871dd754ab3c01c180</b><br>', 'null'],
[-43.73304748535156, 32.15885543823242, '<b><a href="/report/main@9060907d555cecab3519fcbc82318d7e">main</a><br>@9060907d555cecab3519fcbc82318d7e</b><br>', 'null'],
[46.45463180541992, -96.47124481201172, '<b><a href="/report/main@1bf3bcaca0e582026c935549bb7d8a33">main</a><br>@1bf3bcaca0e582026c935549bb7d8a33</b><br>', 'null'],
[17.502174377441406, 66.59679412841797, '<b><a href="/report/main@b9e7701b101639a92238161f00b7471e">main</a><br>@b9e7701b101639a92238161f00b7471e</b><br>', 'null'],

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
mov dword[0x42fcdc], 0x35074
push 0
call dword[sym.imp.KERNEL32.dll_GetModuleHandleW]
mov ecx, dword[0x42fcdc]
add ecx, eax
mov dword[0x42fcdc], ecx
push 0
call dword[sym.imp.KERNEL32.dll_GetConsoleWindow]
push eax
call dword[sym.imp.USER32.dll_ShowWindow]
test eax, eax
je off.b74
push 0x180
mov edx, dword[0x42fcdc]
push edx
call fcn.00401290
add esp, 8
push edx
push eax
push ecx
mov ecx, dword[0x42fcdc]
push ecx
push edx
push eax
push ecx
jmp dword[esp+0xc]

{% endhighlight %}

[virustotal_ref]: https://www.virustotal.com/gui/file/bd5810ea8cdeec913ece5ee7baedb8e9