#
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#101827">
<title>Misba Trading</title>
<style>
*{box-sizing:border-box}
body{
  margin:0;padding:20px;
  font-family:Arial,sans-serif;
  background:#101827;color:#fff;
}
.container{max-width:600px;margin:auto}
header{text-align:center;padding:20px 0}
h1{color:#38d9a9;margin:0;font-size:29px}
.subtitle{color:#9ca3af;font-size:13px}
.card{
  background:#1d293b;border:1px solid #334155;
  border-radius:14px;padding:18px;margin:15px 0;
}
.status{color:#fbbf24;font-size:13px}
h3{margin-top:0;color:#38d9a9}
label{display:block;color:#cbd5e1;margin:12px 0 6px}
input{
  width:100%;padding:13px;border-radius:8px;
  border:1px solid #475569;background:#101827;
  color:white;font-size:16px;
}
button{
  width:100%;padding:14px;margin-top:18px;
  border:0;border-radius:9px;background:#0dba8a;
  color:#071b16;font-weight:bold;font-size:16px;
}
#signal{
  text-align:center;font-size:24px;font-weight:bold;
  padding:18px;border-radius:10px;background:#101827;
}
.note{font-size:12px;color:#94a3b8;line-height:1.6}
</style>
</head>
<body>
<div class="container">

<header>
<h1>MISBA TRADING</h1>
<p class="subtitle">NIFTY Futures | EMA 9 + VWAP</p>
</header>

<div class="card">
<h3>Connection Status</h3>
<p class="status">● DEMO / MANUAL MODE</p>
<p class="note">Live market data is not connected yet.</p>
</div>

<div class="card">
<h3>EMA 9 + VWAP Crossover</h3>

<label>Previous EMA 9</label>
<input id="pe" type="number" step="any" placeholder="Example: 25000">

<label>Previous VWAP</label>
<input id="pv" type="number" step="any" placeholder="Example: 25010">

<label>Current EMA 9</label>
<input id="ce" type="number" step="any" placeholder="Example: 25015">

<label>Current VWAP</label>
<input id="cv" type="number" step="any" placeholder="Example: 25005">

<button onclick="checkSignal()">CHECK SIGNAL</button>
</div>

<div class="card">
<h3>Trading Signal</h3>
<div id="signal">WAITING</div>
<p id="details" class="note">
Enter indicator values to test the crossover.
</p>
</div>

<div class="card">
<h3>Strategy Rules</h3>
<p>🟢 EMA 9 crosses above VWAP = BUY CALL signal</p>
<p>🔴 EMA 9 crosses below VWAP = BUY PUT signal</p>
<p class="note">This is a crossover test only, not a live trading recommendation.</p>
</div>

<p class="note" style="text-align:center">
MISBA TRADING • Version 1.0
</p>
</div>

<script>
function checkSignal(){
 const pe=Number(document.getElementById("pe").value);
 const pv=Number(document.getElementById("pv").value);
 const ce=Number(document.getElementById("ce").value);
 const cv=Number(document.getElementById("cv").value);
 const signal=document.getElementById("signal");
 const details=document.getElementById("details");

 if(["pe","pv","ce","cv"].some(id =>
   document.getElementById(id).value.trim()===""
 )){
   signal.textContent="WAITING";
   details.textContent="Please enter all four values.";
   return;
 }

 if(pe<=pv && ce>cv){
   signal.textContent="BUY CALL 🟢";
   details.textContent="Bullish EMA 9 / VWAP crossover detected.";
 }else if(pe>=pv && ce<cv){
   signal.textContent="BUY PUT 🔴";
   details.textContent="Bearish EMA 9 / VWAP crossover detected.";
 }else{
   signal.textContent="NO SIGNAL";
   details.textContent="No new crossover detected.";
 }
}
</script>
</body>
</html>
Nifty-ema-vwap-cross
Free NIFTY Futures EMA9 + VWAP Crossover Signal App with BUY/SELL Alerts
