# chart.js
This is a customize version created for me. The original repo for chart.js ca be found at https://github.com/nnnick/Chart.js
var chart_data = [],<br/>
    barsCount = 50,<br/>
    labels = new Array(barsCount),<br/>
    updateDelayMax = 500,<br/>
    jQueryid = function(id){<br/>
        return document.getElementById(id);<br/>
    },<br/>
    random = function(max){ return Math.round(Math.random()*100)},<br/>
    helpers = Chart.helpers;<br/>
function Colour(col, amt) {<br/>
    var usePound = false;<br/>
    if (col[0] == "#") {<br/>
        col = col.slice(1);<br/>
        usePound = true;<br/>
    }<br/>
    var num = parseInt(col,16);<br/>
    var r = (num >> 16) + amt;<br/>
    if (r > 255) r = 255;<br/>
    else if  (r < 0) r = 0;<br/>
    var b = ((num >> 8) & 0x00FF) + amt;<br/>
    if (b > 255) b = 255;<br/>
    else if  (b < 0) b = 0;<br/>
    var g = (num & 0x0000FF) + amt;<br/>
    if (g > 255) g = 255;<br/>
    else if (g < 0) g = 0;<br/>
    return (usePound?"#":"") + (g | (b << 8) | (r << 16)).toString(16);<br/>
}<br/>
var colours = {<br/>
    "label 1": "#109618",<br/>
    "label 2": "#3366CC",<br/>
    "label 3": "#6633CC",<br/>
    "label 4": "#CC3333",<br/>
    "label 5": "#FF7C4C",<br/>
    "No Data Found" : "#cccccc"<br/>
};<br/>
var randomScalingFactor = function(){ return Math.round(Math.random()*100)};<br/>
var pie_chart_1 = document.getElementById('pie_chart_1').getContext("2d");<br/>
var pieDatai = [<br/>
    {<br/>
        value: 343,<br/>
        color:colours["label 1"],<br/>
        highlight: Colour(colours["label 1"], 15),<br/>
        label: "label 1"<br/>
    },{<br/>
        value: 478.98,<br/>
        color:colours["label 2"],<br/>
        highlight: Colour(colours["label 2"], 15),<br/>
        label: "label 2"<br/>
    },{<br/>
        value: 35,<br/>
        color:colours["label 3"],<br/>
        highlight: Colour(colours["label 3"], 15),<br/>
        label: "label 3"<br/>
    },{<br/>
        value: 105,<br/>
        color:colours["label 4"],<br/>
        highlight: Colour(colours["label 4"], 15),<br/>
        label: "label 4"<br/>
    }<br/>
];<br/>
myPiei = new Chart(pie_chart_1).Pie(pieDatai, options);<br/>
var legendHolderi = document.getElementById('legend_pie_chart_1');<br/>
legendHolderi.innerHTML = myPiei.generateLegend();<br/>
helpers.each(legendHolderi.firstChild.firstChild.childNodes, function(legendNode, index){<br/>
    helpers.addEvent(legendNode, 'mouseover', function(){<br/>
        var activeSegment = myPiei.segments[index];<br/>
        activeSegment.save();<br/>
        activeSegment.fillColor = activeSegment.highlightColor;<br/>
        myPiei.showTooltip([activeSegment]);<br/>
        activeSegment.restore();<br/>
    });<br/>
});<br/>
helpers.addEvent(legendHolderi.firstChild.firstChild.firstChild, 'mouseout', function(){<br/>
    myPiei.draw();<br/>
});<br/>
document.getElementById('pie_chart_1').parentNode.appendChild(legendHolderi.firstChild);<br/>
<script type="text/javascript" src="chart.js"></script>
<div id="chartdiv1" class="canvas-holde" style="margin:10px auto 0 15px;"><canvas id="pie_chart_1" width="300" height="300"></canvas><div id="legend_pie_chart_1"></div></div>
<script type="text/javascript">
var chart_data = [],
    barsCount = 50,
    labels = new Array(barsCount),
    updateDelayMax = 500,
    jQueryid = function(id){
        return document.getElementById(id);
    },
    random = function(max){ return Math.round(Math.random()*100)},
    helpers = Chart.helpers;
function Colour(col, amt) {
    var usePound = false;
    if (col[0] == "#") {
        col = col.slice(1);
        usePound = true;
    }
    var num = parseInt(col,16);
    var r = (num >> 16) + amt;
    if (r > 255) r = 255;
    else if  (r < 0) r = 0;
    var b = ((num >> 8) & 0x00FF) + amt;
    if (b > 255) b = 255;
    else if  (b < 0) b = 0;
    var g = (num & 0x0000FF) + amt;
    if (g > 255) g = 255;
    else if (g < 0) g = 0;
    return (usePound?"#":"") + (g | (b << 8) | (r << 16)).toString(16);
}
var colours = {
    "label 1": "#109618",
    "label 2": "#3366CC",
    "label 3": "#6633CC",
    "label 4": "#CC3333",
    "label 5": "#FF7C4C",
    "No Data Found" : "#cccccc"
};
var randomScalingFactor = function(){ return Math.round(Math.random()*100)};
var pie_chart_1 = document.getElementById('pie_chart_1').getContext("2d");
var pieDatai = [
    {
        value: 343,
        color:colours["label 1"],
        highlight: Colour(colours["label 1"], 15),
        label: "label 1"
    },{
        value: 478.98,
        color:colours["label 2"],
        highlight: Colour(colours["label 2"], 15),
        label: "label 2"
    },{
        value: 35,
        color:colours["label 3"],
        highlight: Colour(colours["label 3"], 15),
        label: "label 3"
    },{
        value: 105,
        color:colours["label 4"],
        highlight: Colour(colours["label 4"], 15),
        label: "label 4"
    }
];
myPiei = new Chart(pie_chart_1).Pie(pieDatai, options);
var legendHolderi = document.getElementById('legend_pie_chart_1');
legendHolderi.innerHTML = myPiei.generateLegend();
helpers.each(legendHolderi.firstChild.firstChild.childNodes, function(legendNode, index){
    helpers.addEvent(legendNode, 'mouseover', function(){
        var activeSegment = myPiei.segments[index];
        activeSegment.save();
        activeSegment.fillColor = activeSegment.highlightColor;
        myPiei.showTooltip([activeSegment]);
        activeSegment.restore();
    });
});
helpers.addEvent(legendHolderi.firstChild.firstChild.firstChild, 'mouseout', function(){
    myPiei.draw();
});
document.getElementById('pie_chart_1').parentNode.appendChild(legendHolderi.firstChild);
</script>
