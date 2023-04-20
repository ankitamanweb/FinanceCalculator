# FinanceCalculator
Demo and Test Site for Finance Calculations
<!DOCTYPE html>
<html>
<head>
	<title>SIP Calculator</title>
</head>
<body>
	<h1>SIP Calculator</h1>
	<form>
		<label for="principal">Investment Amount:</label>
		<input type="number" id="principal" name="principal" required><br><br>

		<label for="rate">Expected Annual Return (%):</label>
		<input type="number" id="rate" name="rate" required><br><br>

		<label for="time">Duration of Investment (in years):</label>
		<input type="number" id="time" name="time" required><br><br>

		<label for="sip">SIP Frequency:</label>
		<select id="sip" name="sip">
			<option value="monthly">Monthly</option>
			<option value="quarterly">Quarterly</option>
			<option value="halfyearly">Half Yearly</option>
			<option value="yearly">Yearly</option>
		</select><br><br>

		<label for="total">Total Investment:</label>
		<input type="number" id="total" name="total" readonly><br><br>

		<label for="maturity">Maturity Value:</label>
		<input type="number" id="maturity" name="maturity" readonly><br><br>

		<button type="button" onclick="calculate()">Calculate</button>
	</form>

	<script>
		function calculate() {
			// Get the input values
			var principal = document.getElementById("principal").value;
			var rate = document.getElementById("rate").value;
			var time = document.getElementById("time").value;
			var sip = document.getElementById("sip").value;

			// Calculate the total investment
			var total = 0;
			if(sip == "monthly") {
				total = principal * 12 * time;
			}
			else if(sip == "quarterly") {
				total = principal * 4 * time;
			}
			else if(sip == "halfyearly") {
				total = principal * 2 * time;
			}
			else if(sip == "yearly") {
				total = principal * time;
			}
			document.getElementById("total").value = total.toFixed(2);

			// Calculate the maturity value
			var maturity = principal * Math.pow(1 + (rate/100), time);
			document.getElementById("maturity").value = maturity.toFixed(2);
		}
	</script>
</body>
</html>
