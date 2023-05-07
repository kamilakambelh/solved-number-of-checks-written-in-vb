Download Link: https://assignmentchef.com/product/solved-number-of-checks-written-in-vb
<br>
<p class="ui header product-top-header" title="Number of checks written Solution">A bank charges $10 per month plus the following check fees for a commercial checking account:

$0.10 each for less than 20 checks, $0.08 each for 20-39 checks, $0.06 each for 40-59 checks $0.04 each for 60 or more checks.

Create an application that allows the user to enter the number of checks written. The application should compute and display the bank’s sevice fees for the month. All checks for the month are assigned the same charge, based on the total number of checks written during the month.

Input validation: Do not accept a negative value for the number of checks written. Ensure that all values are numeric. The Clear button must clear the text box and the label that displays the monthly service charge.

Use the following test data to determine if the application is calculating properly.

The integers are the number of checks that are entered in the textbox by the user.

15 ———— $ 11. 50

25————-$12.00

45————-$12.70

75————-$13.00

The code:

Public Class Form1

Private Sub btnCalculate_Click(sender As Object, e As EventArgs) Handles btnCalculate.Click

Dim decBaseFee As Decimal ‘Base Monthly Fee

Dim decTotalServiceFee As Integer ‘Total Service Fee

Dim intChecks As Integer ‘Number of Checks

Dim blnInputOk As Boolean = True

Const decSERVICE_FEE As Decimal = 10D

Const decLESS_THAN_TWENTY As Decimal = 0.1D

Const decTWENTY_TO_THIRTY_NINE As Decimal = 0.08D

Const decFORTY_TO_FIFTY_NINE As Decimal = 0.06D

Const decSIXTY_OR_MORE As Decimal = 0.04D

‘Validate and ensure all values are numeric

If Integer.TryParse(txtChecks.Text, intChecks) = False Then

lblStatus.Text = “Checks must be an integer.”

blnInputOk = False

End If

‘Validate the number of checks. Do not accept a negative value.

If intChecks &lt; 0 Then

lblStatus.Text = “Checks must be positive.”

blnInputOk = False

End If

If blnInputOk = True Then

‘Determine the fees for each range.

If intChecks &lt; 20 Then

decBaseFee = intChecks * decLESS_THAN_TWENTY

ElseIf intChecks = 20 And intChecks &lt;= 39 Then

decBaseFee = intChecks * decTWENTY_TO_THIRTY_NINE

ElseIf intChecks = 40 And intChecks &lt;= 59 Then

decBaseFee = intChecks * decFORTY_TO_FIFTY_NINE

ElseIf intChecks = 60 Then

decBaseFee = intChecks * decSIXTY_OR_MORE

End If

‘Calculate the total service fee.

decTotalServiceFee = decBaseFee + decSERVICE_FEE

‘Display the fee.

lblMonthlyFee.Text = decTotalServiceFee.ToString(“C”)

End If

End Sub

Private Sub btnExit_Click(sender As Object, e As EventArgs) Handles btnExit.Click

‘Close the form.

Me.Close()

End Sub

Private Sub btnClear_Click(sender As Object, e As EventArgs) Handles btnClear.Click

‘Clear the number of checks.

txtChecks.Clear()

‘Clear the fee label.

lblMonthlyFee.Text = String.Empty

End Sub

End Class