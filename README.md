<!DOCTYPE html>
<html>
<h1>RxErT's Calculator</h1>
<h2>HTML - ( CSS soon )</h2>
<h3>Made on 3/11/2018 at 12:30 AM</h3>

<body>
    <FORM name="Keypad" action="">
<input name="ReadOut" id="output" type="Text" size=24 value="0" readonly>
    <table>
<tr>
  <td><input id="btn7" type="Button" value="  7  " onclick="NumPressed(7)"></td>
  <td><input id="btn8" type="Button" value="  8  " onclick="NumPressed(8)"></td>        
  <td><input id="btn9" type="Button" value="  9  " onclick="NumPressed(9)"></td>
<td colspan="2"><input id="btnC" type="Button" value="  C  " onclick="Clear()"></td>
</tr>
<tr>
  <td><input id="btn4" type="Button" value="  4" onclick="NumPressed(4)"></td>
  <td><input id="btn5" type="Button" value="  5   "onclick="NumPressed(5)"></td>        
  <td><input id="btn6" type="Button" value="  6  " onclick="NumPressed(6)"></td>
<td><input id="btnplusminus" type="Button" value=" +/- " onclick="Neg()"></td>
<td><input id="btnplus" type="Button" value="  +  " onclick="Operation('+')"></td>
</tr>
<tr>
  <td><input id="btn1" type="Button" value="  1  " onclick="NumPressed(1)"></td>
  <td><input id="btn2" type="Button" value="  2  " onclick="NumPressed(2)"></td>        
  <td><input id="btn3" type="Button" value="  3  " onclick="NumPressed(3)"></td>
<td><input id="btnmultiply" type="Button" value="  *  " onclick="Operation('*')"></td>
<td><input id="btnminus" type="Button" value="   -   " onclick="Operation('-')"></td>
</tr>
</table>
<input id="btn0" type="Button" value="  0  " onclick="NumPressed(0)">
  <input id="btndecimal" type="Button" value="   .  " onclick="Decimal()">      
<input id="btndivide" type="Button" value="   /   " onclick="Operation('/')">
<input id="about" type="Button" value="About" onclick="myFunction()"></br>
<input id="btnequals" type="Button" value="  =  " onclick="Operation('=')">
 </FORM>

<script>
var FKeyPad = document.Keypad;
var Accumulate = 0;
var FlagNewNum = false;
var PendingOp = "";
function NumPressed (Num) {
if (FlagNewNum) {
FKeyPad.ReadOut.value  = Num;
FlagNewNum = false;
   }
else {
if (FKeyPad.ReadOut.value == "0")
FKeyPad.ReadOut.value = Num;
else
FKeyPad.ReadOut.value += Num;
   }
}
function Operation (Op) {
var Readout = FKeyPad.ReadOut.value;
if (FlagNewNum && PendingOp != "=");
else
{
FlagNewNum = true;
if ( '+' == PendingOp )
Accumulate += parseFloat(Readout);
else if ( '-' == PendingOp )
Accumulate -= parseFloat(Readout);
else if ( '/' == PendingOp )
Accumulate /= parseFloat(Readout);
else if ( '*' == PendingOp )
Accumulate *= parseFloat(Readout);
else
Accumulate = parseFloat(Readout);
FKeyPad.ReadOut.value = Accumulate;
PendingOp = Op;
   }
}
function Decimal () {
var curReadOut = FKeyPad.ReadOut.value;
if (FlagNewNum) {
curReadOut = "0.";
FlagNewNum = false;
   }
else
{
if (curReadOut.indexOf(".") == -1)
curReadOut += ".";
   }
FKeyPad.ReadOut.value = curReadOut;
}
function ClearEntry () {
FKeyPad.ReadOut.value = "0";
FlagNewNum = true;
}
function Clear () {
Accumulate = 0;
PendingOp = "";
ClearEntry();
}
function Neg () {
FKeyPad.ReadOut.value = parseFloat(FKeyPad.ReadOut.value) * -1;
}
function Percent () {
FKeyPad.ReadOut.value = (parseFloat(FKeyPad.ReadOut.value) / 100) * parseFloat(Accumulate);
}
</script>
