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
    [92.40653991699219, 43.33279800415039, '<b><a href="/report/main@bd5810ea8cdeec913ece5ee7baedb8e9">main</a><br>@bd5810ea8cdeec913ece5ee7baedb8e9</b><br>', 'point { fill-color: #e0440e; }'],
[13.776412963867188, 55.31100845336914, '<b><a href="/report/main@0606e50385fe518042f9ea006b816a98">main</a><br>@0606e50385fe518042f9ea006b816a98</b><br>', 'null'],
[64.7103042602539, -121.09850311279297, '<b><a href="/report/main@e9c6b3bcaa2edc455cb26f1e0f4a513a">main</a><br>@e9c6b3bcaa2edc455cb26f1e0f4a513a</b><br>', 'null'],
[83.60100555419922, -50.88578796386719, '<b><a href="/report/main@773e84b03dfb92871dd754ab3c01c180">main</a><br>@773e84b03dfb92871dd754ab3c01c180</b><br>', 'null'],
[133.0574951171875, -92.6905746459961, '<b><a href="/report/main@6312517583453b51c66fd5c06a181092">main</a><br>@6312517583453b51c66fd5c06a181092</b><br>', 'null'],
[45.16950607299805, -2.105975866317749, '<b><a href="/report/main@8db9fe0b752fe464ff1c81507df8551a">main</a><br>@8db9fe0b752fe464ff1c81507df8551a</b><br>', 'null'],
[136.7659149169922, -12.50661563873291, '<b><a href="/report/main@8fe319558c6f221efde51f3acc33b19c">main</a><br>@8fe319558c6f221efde51f3acc33b19c</b><br>', 'null'],
[22.6517391204834, -60.38388442993164, '<b><a href="/report/main@b9e7701b101639a92238161f00b7471e">main</a><br>@b9e7701b101639a92238161f00b7471e</b><br>', 'null'],
[-7.779134273529053, -118.61138916015625, '<b><a href="/report/main@1bf3bcaca0e582026c935549bb7d8a33">main</a><br>@1bf3bcaca0e582026c935549bb7d8a33</b><br>', 'null'],
[-26.753629684448242, -5.2890448570251465, '<b><a href="/report/main@31d828bf241be93b3ffe89cf3c313d44">main</a><br>@31d828bf241be93b3ffe89cf3c313d44</b><br>', 'null'],
[-48.98757553100586, -65.2298812866211, '<b><a href="/report/main@9060907d555cecab3519fcbc82318d7e">main</a><br>@9060907d555cecab3519fcbc82318d7e</b><br>', 'null'],

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
je 0x40152a
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