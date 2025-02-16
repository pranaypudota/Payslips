# Payroll Automation Script

This Google Apps Script automates monthly payroll processing by sending HTML email payslips based on last month's data. It calculates each employee's total salary after adding incentives and subtracting holiday and utility deductions. Processed payroll records are archived in a separate "Payroll History" sheet, while the main sheet retains persistent employee details (Name & Email) for future cycles.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Calculation Logic](#calculation-logic)
- [Setup & Installation](#setup--installation)
- [Usage](#usage)
- [Error Handling](#error-handling)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This script reads payroll data from a Google Sheet with columns for Employee Name, Email, Salary, Incentives, and Holidays. It computes the total payable salary for each employee using last month’s data (since salaries are paid with a one-month lag) and sends an HTML email payslip. After processing, the monthly fields are cleared from the main sheet while historical data (with a month label) is appended to the "Payroll History" sheet.

---

## Key Features

- **Automated Payslip Dispatch:**  
  Sends an HTML email to each employee containing detailed payroll information.

- **Salary Calculation:**  
  - **Salary After Incentives:** Base Salary + Incentives  
  - **Holiday Deduction:** Number of Holidays Taken × ₹500  
  - **Utility Deduction:** Fixed at ₹300  
  - **Total Salary:** (Salary + Incentives) – (Holiday Deduction + Utility Deduction)

- **Payroll History Management:**  
  Processed records are archived in a separate "Payroll History" sheet. Only the monthly payroll data fields are cleared from the main sheet, preserving core employee details for new or continuing entries.

- **User Interface Enhancements:**  
  - Custom menu for dispatching payslips.
  - Zebra striping for improved sheet readability.

---

## Calculation Logic

| Component                   | Formula                                                | Notes                         |
|-----------------------------|--------------------------------------------------------|-------------------------------|
| Salary After Incentives     | Salary + Incentives                                    | Increases the base salary     |
| Holiday Deduction           | Holidays × ₹500                                        | Deducts per day of leave      |
| Utility Deduction           | Fixed amount of ₹300                                   | Same for every employee       |
| Total Salary                | (Salary + Incentives) - (Holiday + Utility Deduction)  | Final payable amount        |

---

## Setup & Installation

1. **Prepare Your Google Spreadsheet:**  
   Create or use an existing sheet with these required headers (order can vary):
   - Employee Name
   - Email
   - Salary
   - Incentives
   - Holidays

2. **Access the Script Editor:**  
   In your Google Sheet, navigate to **Extensions > Apps Script**.

3. **Add the Script:**  
   Copy the final code into the script editor and save your project.

4. **Authorize the Script:**  
   Run the `onOpen` function to trigger authorization. Follow the prompts to grant the necessary permissions.

5. **Reload the Spreadsheet:**  
   This ensures that the custom "Payslips" menu appears in the UI.

---

## Usage

1. **Enter Payroll Data:**  
   Populate the main sheet with the latest payroll details for each employee.

2. **Dispatch Payslips:**  
   - Click **Payslips > Dispatch Payslips** from the custom menu.
   - The script processes each row, calculates the total salary based on last month's data, and sends out HTML-formatted payslips.
   - Once complete, processed data is archived in the "Payroll History" sheet, and the monthly data fields (Salary, Incentives, Holidays) are cleared from the main sheet.

3. **Review Payroll History:**  
   The "Payroll History" sheet maintains a log of each payroll run with a "Month" label for reference.

---

## Error Handling

- **Missing Columns:**  
  If any required columns (Employee Name, Email, Salary, Incentives, Holidays) are missing, the script throws an error and alerts the user.

- **Row-Level Errors:**  
  For each row, if essential details (like Email or Employee Name) are missing or if the email format is invalid, the error is logged and processing continues with the next row.

- **Global Errors:**  
  If a critical error occurs during processing, an email is sent to a designated address (e.g., `abcdefg@gmail.com`) and an alert is shown in the spreadsheet UI.


---

## Contributing

Contributions and suggestions are welcome! To contribute:
- Fork this repository.
- Create a new branch for your changes.
- Submit a pull request with detailed notes on your modifications.

For any issues or feature requests, please open an issue on GitHub.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

Happy automating!

         
