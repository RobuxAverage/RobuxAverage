<title>ROBUXAVERAGE</title>
<script>
google.charts.load('current', {packages: ['corechart', 'line']});
google.charts.setOnLoadCallback(drawBasic);

document.querySelector("input").addEventListener("keypress", function (evt) {
    if (evt.which < 48 || evt.which > 57)
    {
        evt.preventDefault();
    }
});

function drawBasic() {

      var data = new google.visualization.DataTable();
      data.addColumn('number', 'X');
      data.addColumn('number', "ROBUX to $1");

      data.addRows([
        [0, 0],   [1, 10],  [2, 23],  [3, 17],  [4, 18],  [5, 9],
        [6, 11],  [7, 27],  [8, 33],  [9, 40],  [10, 32], [11, 35],
        [12, 30], [13, 40], [14, 42], [15, 47], [16, 44], [17, 48],
        [18, 52], [19, 54], [20, 42], [21, 55], [22, 56], [23, 57],
        [24, 60], [25, 50], [26, 52], [27, 51], [28, 49], [29, 53],
        [30, 55], [31, 60], [32, 61], [33, 59], [34, 62], [35, 65],
        [36, 62], [37, 58], [38, 55], [39, 61], [40, 64], [41, 65],
        [42, 63], [43, 66], [44, 67], [45, 69], [46, 69], [47, 70],
        [48, 72], [49, 68], [50, 66], [51, 65], [52, 67], [53, 70],
        [54, 71], [55, 72], [56, 73], [57, 75], [58, 70], [59, 68],
        [60, 64], [61, 60], [62, 65], [63, 67], [64, 68], [65, 69],
        [66, 70], [67, 72], [68, 75], [69, 80]
      ]);

      var options = {
        hAxis: {
          title: 'Time'
        },
        vAxis: {
          title: 'Amount'
        }
      };

      var chart = new google.visualization.LineChart(document.getElementById('chart_div'));

      chart.draw(data, options);
    }

function requestAmt() {
  var lowamt = 80
  var lowusd = 0.99
  var highamt = 450
  var highusd = 4.99
  var amt = document.getElementById('rbx-val').value;
  var i = amt / lowamt * lowusd;
  var j = amt / highamt * highusd;
  var k = i + j;
  var l = k / 2
  var usd = l.toFixed(2);
  document.getElementById('aprox-usd').innerHTML = usd + " USD";
  document.getElementById('bought-for').innerHTML = "Have <span>" + amt + " </span>ROBUX? <a href='/sell?amt=" + amt + "'><b>Sell it for "+ usd / 4 + " USD</b></a>" + "!";
}

setInterval(function() {
  requestAmt()
}, 0);
</script>
<body onload="setInterval(function() { requestAmt() }, 0); chart.draw(data, options);">
<style>
@import url(https://fonts.googleapis.com/css?family=Open+Sans);

body {
   font-family: 'Open Sans',serif;
   background-color: white;
}

input
{
    width:200px;
    font-size:14pt;
}

a {
    color: #3399ff;
    text-decoration: none;
}

h1 {
    font-size: 50px;
}

.top {
    background-color: black;
    text-indent: 35px;
}

.background {
    background-color: #42f4b6;
}

textarea:focus, input:focus{
    outline: none;
}

input[type=text] {
    width: 20%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ddd;
    border-radius: 5px;
    box-sizing: border-box;
}

input[type=text]:hover, input[type=text]:focus {
    width: 20%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #3399ff;
    border-radius: 5px;
    box-sizing: border-box;
}
</style>
<div class="top"><br>
<font color="white"><b><p>R O B U X A V E R A G E</p></b><br></font>
</div>
<div class="background">
<center>
<input maxlength="22" type="text" value="1000" id="rbx-val"></center>
</div>
<h1 id="aprox-usd"></h1>
<p id="bought-for"></p>
<div id="chart_div"></div>
<b>Top Buyers</b><br>
<center><font color="gray"><i>There are no top buyers.</i></font></center>
