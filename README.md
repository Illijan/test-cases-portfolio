# Warehouse Management System (WMS) - QA Documentation

This repository contains test documentation, including Test Scenarios and Test Cases, created for a Warehouse Management System (WMS). It demonstrates my ability to analyze requirements, design structured test cases, and apply QA methodologies using tools like Jira and Testomat.io/Zephyr.

---

## Project Overview & Testing Approach
*   **Module Tested:** Inventory Management & Outbound Processing.
*   **Methodology:** Agile (Kanban).
*   **Tools Used for Documentation:** Jira, Zephyr Scale / Testomat.io formats.
*   **Testing Types:** Functional Testing, Positive/Negative Testing, Boundary Value Analysis.

---

## Test Cases (Jira / Zephyr Format)

Below are examples of manual test cases documenting core WMS business logic.

### TC-001: Successfully add new incoming stock to inventory (Positive)

**Preconditions:**
1. User is logged into the WMS with `Warehouse Manager` permissions.
2. The product SKU `SKU-9988` exists in the system database.

| Step | Action | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Navigate to the "Inbound Receiving" module from the main dashboard. | The "Inbound Receiving" page is loaded successfully. | As expected. | Pass |
| **2** | Scan or manually enter the barcode `SKU-9988` into the "Item ID" field and press Enter. | Product details (Name, Category, Current Stock) are populated on the screen. | As expected. | Pass |
| **3** | Enter `50` in the "Quantity Received" field. | The field accepts the numeric value. | As expected. | Pass |
| **4** | Select Zone `A`, Rack `12` from the "Storage Location" dropdown. | Location is selected and highlighted. | As expected. | Pass |
| **5** | Click the "Confirm Receipt" button. | A success message "Stock updated successfully" is displayed. Total inventory for `SKU-9988` increases by 50 units. | As expected. | Pass |

---

### TC-002: Prevent outbound shipment exceeding current stock (Negative)

**Preconditions:**
1. User is logged in as `Fulfillment Specialist`.
2. Product `SKU-1122` currently has exactly `10` units in stock.

| Step | Action | Expected Result | Actual Result | Status |
| :--- | :--- | :--- | :--- | :--- |
| **1** | Navigate to the "Outbound / Dispatch" module. | The "Outbound Orders" page is loaded. | As expected. | Pass |
| **2** | Create a new dispatch order and add `SKU-1122` to the item list. | Item is added to the draft order. | As expected. | Pass |
| **3** | Enter `15` in the "Dispatch Quantity" field (which is greater than the available stock of 10). | System registers the input. | As expected. | Pass |
| **4** | Click the "Process Shipment" button. | The system blocks the action and displays a red validation error: *"Error: Insufficient stock. Available: 10"*. The order status remains "Draft". | As expected. | Pass |

---

## Defect Tracking & Bug Reports
When a test case fails, a detailed bug report is created and linked directly to the specific execution run in Jira. 

**[Click here to view my Bug Report Portfolio](https://github.com/Illijan/bug-report-portfolio)** to see examples of how I document defects with steps to reproduce, priority, and visual evidence.
