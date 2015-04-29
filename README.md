# chart.js
This is a customize version created for me. The original repo for chart.js can be found at https://github.com/nnnick/Chart.js 
<pre>var chart_data = [],
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
<script type="text/javascript" src="chart.js"></script>
<div id="chartdiv1" class="canvas-holde" style="margin:10px auto 0 15px;"><canvas id="pie_chart_1" width="300" height="300"></canvas><div id="legend_pie_chart_1"></div></div>
<pre>
