# Control Flow Diagram (CFD) - Vehicle Maintenance and Service System

## Level 0: System Context Diagram

```
                           ┌─────────────┐
                           │   ADMIN     │
                           └──────┬──────┘
                                  │
                    • System Setup │ System Reports
                    • User Management
                                  │
                                  ▼
                    ┌─────────────────────────────┐
                    │                             │
                    │  VEHICLE MAINTENANCE AND    │
                    │  SERVICE SYSTEM             │
                    │                             │
                    └─────────────────────────────┘
                                  ▲
                                  │
                    • Analytics   │ Audit Logs
                    • Notifications


       ┌─────────────┐              ┌──────────────┐
       │  CUSTOMER   │              │SERVICE STAFF │
       │  (CLIENT)   │              │ (TECHNICIAN) │
       └──────┬──────┘              └──────┬───────┘
              │                            │
   Service Info│        System        │Service Updates
   Bookings    │       Manage         │Work Records
              │                            │
              ▼                            ▼
              ┌─────────────────────────────┐
              │                             │
              │  VEHICLE MAINTENANCE AND    │
              │  SERVICE SYSTEM             │
              │                             │
              └─────────────────────────────┘
              │              ▲              │
              │              │              │
   Confirmation│  Database   │Records      │Invoices
   History     │  Storage    │Payment      │Receipts
              │              │             │
              ▼              │             ▼
   ┌─────────────────────────────────────────────┐
   │           DATABASE (All Records)             │
   │  • Customers  • Vehicles  • Services         │
   │  • Technicians• Payments  • Invoices         │
   └─────────────────────────────────────────────┘
              │
              │
              ▼
   ┌──────────────────────────────────────────┐
   │      EXTERNAL SERVICES                   │
   │  • Payment Gateway  • Email Service       │
   │  • SMS Service      • Backup Storage      │
   └──────────────────────────────────────────┘
```

---

## Level 1: Main Process Flows

### Customer Flow

```
┌─────────────────┐
│   CUSTOMER      │
│   (Login)       │
└────────┬────────┘
         │
         ▼
    ┌─────────┐
    │ SELECT  │
    │ VEHICLE │
    └────┬────┘
         │
         ▼
    ┌──────────────┐
    │   SCHEDULE   │
    │ MAINTENANCE  │
    └────┬────────┘
         │
         ▼
    ┌──────────────┐
    │   CONFIRM    │
    │  & PAYMENT   │
    └────┬────────┘
         │
         ▼
    ┌──────────────┐
    │   RECEIVE    │
    │  CONFIRMATION│
    └──────────────┘
```

### Service Staff Flow

```
┌─────────────────┐
│  SERVICE STAFF  │
│   (Login)       │
└────────┬────────┘
         │
         ▼
    ┌─────────┐
    │  VIEW   │
    │  TASKS  │
    └────┬────┘
         │
         ▼
    ┌──────────────┐
    │   START      │
    │  SERVICE     │
    └────┬────────┘
         │
         ▼
    ┌──────────────┐
    │  PERFORM     │
    │  WORK        │
    └────┬────────┘
         │
         ▼
    ┌──────────────┐
    │  COMPLETE    │
    │  & REPORT    │
    └──────────────┘
```

### Admin Flow

```
┌─────────────────┐
│   ADMIN         │
│   (Login)       │
└────────┬────────┘
         │
         ▼
    ┌──────────────┐
    │  MANAGE      │
    │  USERS       │
    └────┬────────┘
         │
         ▼
    ┌──────────────┐
    │  SET UP      │
    │  SERVICES    │
    └────┬────────┘
         │
         ▼
    ┌──────────────┐
    │  VIEW        │
    │  REPORTS     │
    └──────────────┘
```

---

## Level 2: Detailed Flows

### Vehicle Registration

```
         ┌─────────────────┐
         │    CUSTOMER     │
         │(Register Vehicle)│
         └────────┬────────┘
                  │
        Enter Vehicle Details
        (License Plate, Make, Model, VIN)
                  │
                  ▼
         ┌─────────────────┐
         │   VALIDATION    │
         └────┬────────────┘
              │
      ┌───────┴───────┐
      │               │
   Valid?          Invalid?
      │               │
      ▼               ▼
  Continue       Show Error
      │               │
      └───────┬───────┘
              │
              ▼
      ┌──────────────┐
      │ SAVE TO      │
      │ DATABASE     │
      └────┬─────────┘
           │
           ▼
      ┌──────────────┐
      │ CONFIRMATION │
      └──────────────┘
```

### Schedule Service

```
         ┌─────────────────┐
         │    CUSTOMER     │
         │(Schedule Service)│
         └────────┬────────┘
                  │
        Select Vehicle & Service Type
        Enter Date & Time
                  │
                  ▼
         ┌─────────────────┐
         │   CHECK IF      │
         │   AVAILABLE     │
         └────┬────────────┘
              │
      ┌───────┴─────────┐
      │                 │
   Available?         Not Available
      │                 │
      ▼                 ▼
  Continue         Suggest Other
      │             Dates
      │                 │
      └────────┬────────┘
               │
               ▼
      ┌──────────────────┐
      │ CALCULATE COST   │
      └────┬─────────────┘
           │
           ▼
      ┌────────���─────────┐
      │ CONFIRM BOOKING  │
      │ & TAKE PAYMENT   │
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ SEND CONFIRMATION│
      │ (Email/SMS)      │
      └──────────────────┘
```

### Service Execution

```
      ┌──────────────────┐
      │  SERVICE STAFF   │
      │ (View Assignment)│
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ RETRIEVE VEHICLE │
      │ & SERVICE DETAILS│
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ START SERVICE    │
      │ (Record Time)    │
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ INSPECT VEHICLE  │
      │ PERFORM WORK     │
      │ TRACK PARTS USED │
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ QUALITY CHECK    │
      │ & APPROVAL       │
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ COMPLETE SERVICE │
      │ GENERATE REPORT  │
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ CREATE INVOICE   │
      │ & SEND TO PAYMENT│
      └──────────────────┘
```

### Payment Processing

```
      ┌──────────────────┐
      │    CUSTOMER      │
      │ (Payment Page)   │
      └────┬─────────────┘
           │
        Invoice Amount
           │
           ▼
      ┌──────────────────┐
      │ SELECT PAYMENT   │
      │ METHOD           │
      │ (Card/Cash/Bank) │
      └────┬─────────────┘
           │
           ▼
      ┌��─────────────────┐
      │ PROCESS PAYMENT  │
      │ (via Gateway)    │
      └────┬─────────────┘
           │
      ┌────┴─────────┐
      │              │
   Success         Failed
      │              │
      ▼              ▼
  Continue       Retry/Cancel
      │              │
      └────┬─────────┘
           │
           ▼
      ┌──────────────────┐
      │ UPDATE INVOICE   │
      │ STATUS: PAID     │
      └────┬─────────────┘
           │
           ▼
      ┌──────────────────┐
      │ SEND RECEIPT     │
      │ (Email/SMS/Print)│
      └──────────────────┘
```

---

## System Components

```
┌─────────────────────────────────────────────────────┐
│         VEHICLE MAINTENANCE SYSTEM                  │
├─────────────────────────────────────────────────────┤
│                                                     │
│  ┌───────────────────────────────────────────────┐  │
│  │  USER MANAGEMENT                              │  │
│  │  ├─ Customer Registration                     │  │
│  │  ├─ Staff Management                          │  │
│  │  └─ Admin Control                             │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
│  ┌───────────────────────────────────────────────┐  │
│  │  VEHICLE MANAGEMENT                           │  │
│  │  ├─ Register Vehicles                         │  │
│  │  ├─ Track History                             │  │
│  │  └─ Maintenance Schedule                      │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
│  ┌───────────────────────────────────────────────┐  │
│  │  SERVICE MANAGEMENT                           │  │
│  │  ├─ Schedule Services                         │  │
│  │  ├─ Assign Technicians                        │  │
│  │  └─ Track Execution                           │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
│  ┌───────────────────────────────────────────────┐  │
│  │  PAYMENT & BILLING                            │  │
│  │  ├─ Generate Invoices                         │  │
│  │  ├─ Process Payments                          │  │
│  │  └─ Send Receipts                             │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
│  ┌───────────────────────────────────────────────┐  │
│  │  DATABASE & STORAGE                           │  │
│  │  ├─ Customer Data                             │  │
│  │  ├─ Vehicle Data                              │  │
│  │  ├─ Service Records                           │  │
│  │  ├─ Payments & Invoices                       │  │
│  │  └─ Audit Logs                                │  │
│  └───────────────────────────────────────────────┘  │
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## Key Entities

```
CUSTOMER
├─ Customer ID
├─ Name, Email, Phone
├─ Address
└─ Vehicle List

VEHICLE
├─ Vehicle ID
├─ License Plate, VIN
├─ Make, Model, Year
├─ Owner (Customer)
└─ Service History

SERVICE REQUEST
├─ Request ID
├─ Vehicle ID
├─ Service Type
├─ Date & Time
├─ Technician Assigned
└─ Status

SERVICE EXECUTION
├─ Start Time
├─ End Time
├─ Work Performed
├─ Parts Used
├─ Labor Hours
└─ Quality Approval

INVOICE/PAYMENT
├─ Invoice ID
├─ Service ID
├─ Amount
├─ Payment Method
├─ Status (Paid/Pending)
└─ Receipt Details
```

---

## Data Flow Summary

```
Customer Input
     │
     ▼
System Process (Validation, Calculation, Storage)
     │
     ▼
Database Storage (Save Records)
     │
     ▼
Send Notifications (Email, SMS)
     │
     ▼
Display Confirmation to User
```

---

## Notes

- All operations are logged in database
- Customers receive email/SMS confirmations
- Payment must be successful before service completion
- Admin has full system visibility and control
- System maintains audit trail of all transactions
