# Control Flow Diagram (CFD) - Vehicle Maintenance and Service System

## Level 0: System Context Diagram

```
                           ┌─────────────┐
                           │   ADMIN     │
                           └──────┬──────┘
                                  │
                    ┌─────────────┬┴──────────────────┐
                    │             │                  │
         • System Config    • User Management   • Reports
         • Role Assignment  • Staff Management  • Analytics
         • Pricing Setup    • Permissions       • Audit Logs
         • Maintenance      • System Settings   • Performance
           Schedule         • Database Config   • Alerts
         • Service Types    • Backup/Recovery   • System Health
         • Notification     • Payment Settings  • User Activity
           Settings         • Integration Setup
         • Working Hours
         • System Alerts
                    │             │                  │
                    └──────────────┬──────────────────┘
                                   │
                    ┌──────────────────────────────────┐
                    │                                  │
                    │  VEHICLE MAINTENANCE AND         │
                    │  SERVICE SYSTEM (CORE)           │
                    │                                  │
                    │  ├─ User Management              │
                    │  ├─ Vehicle Registration         │
                    │  ├─ Maintenance Scheduling       │
                    │  ├─ Service Execution            │
                    │  ├─ Payment Processing           │
                    │  ├─ Inventory Management         │
                    │  ├─ Report Generation            │
                    │  ├─ Notification Engine          │
                    │  ├─ Database Management          │
                    │  └─ Audit & Logging              │
                    │                                  │
                    └──────────────────────────────────┘
                        │            │            │
         ┌──────────────┼────────────┼────────────┼──────────────┐
         │              │            │            │              │
         ▼              ▼            ▼            ▼              ▼
    ┌─────────┐  ┌──────────┐  ┌────────────┐  ┌──────────┐  ┌──────────┐
    │CUSTOMER │  │ SERVICE  │  │ SUPPLIERS/ │  │ PAYMENT  │  │ EXTERNAL │
    │         │  │ STAFF    │  │ INVENTORY  │  │ GATEWAY  │  │SERVICES  │
    │         │  │(TECH)    │  │ STAFF      │  │          │  │          │
    └────┬────┘  └────┬─────┘  └────┬───────┘  └────┬─────┘  └────┬─────┘
         │            │             │               │             │
    • Vehicle Info    • Service    • Stock Info   • Payment    • SMS
    • Maintenance     Requests     • Orders        Processing   • Email
      Schedule        • Service    • Suppliers   • Transaction • API
    • Service History Reports      • Pricing      Records      Integration
    • Bookings        • Timesheets • Invoices   • Receipts    • Backup
    • Payments        • Work       • Stock      • Confirmations  Services
    • Receipts          Orders       Levels
    • Invoices        • Vehicle    • Supply
    • Notifications     Updates      Chain Info
    • Profile           • Parts
      Management        Usage
    • Request Status   • Quality
                       Reports
         │            │             │               │             │
         └────────────┴─────────────┴───────────────┴─────────────┘
```

---

## Level 1: Customer Module Flow

```
                    ┌��────────────────┐
                    │    CUSTOMER     │
                    └────────┬────────┘
                             │
                    ┌─────────┴─────────┐
                    │                   │
         • Login/Registration    • Vehicle Management
         • Credentials           • Schedule Service
         • Profile Info          • View History
                    │                   │
                    └─────────┬─────────┘
                              │
              ┌───────────────────────────┐
              │ CUSTOMER MODULE           │
              ├───────────────────────────┤
              │ • Authentication          │
              │ • Profile Management      │
              │ • Vehicle Registry        │
              │ • Service Scheduling      │
              │ • Order Management        │
              │ • Invoice/Receipt Viewing │
              │ • Notification Prefs      │
              │ • Support Requests        │
              └─────────┬─────────────────┘
                        │
           ┌────────────┼────────────┐
           │            │            │
           ▼            ▼            ▼
    ┌─────────┐  ┌──────────┐  ┌────────────┐
    │VEHICLE  │  │SERVICE   │  │ PAYMENT &  │
    │DATABASE │  │DATABASE  │  │ INVOICE    │
    │         │  │          │  │ DATABASE   │
    ├─────────┤  ├──────────┤  ├────────────┤
    │• VIN    │  │• Type    │  │• Invoice#  │
    │• Make   │  │• Date    │  │• Amount    │
    │• Model  │  │• Status  │  │• Status    │
    │• Owner  │  │• Cost    │  │• Method    │
    │• Mileage│  │• Assign  │  │• Receipt   │
    │• History│  │  Tech    │  │• Payment   │
    │         │  │• Notes   │  │  Status    │
    └─────────┘  └──────────┘  └────────────┘
           │            │            │
           └────────────┼────────────┘
                        │
        • Confirmation Email/SMS
        • Service Updates
        • Payment Receipt
        • Invoice Details
        • Appointment Reminders
                        │
                        ▼
                    ┌─────────────┐
                    │   CUSTOMER  │
                    │ (Dashboard) │
                    └─────────────┘
```

---

## Level 1: Service Staff Module Flow

```
                    ┌──────────────┐
                    │ SERVICE STAFF│
                    │  (TECHNICIAN)│
                    └────────┬─────┘
                             │
                    ┌─────────┴──────────┐
                    │                    │
         • Start Service        • Update Work
         • View Assignments     • Complete Service
         • Access Vehicle Info  • Generate Reports
                    │                    │
                    └─────────┬──────────┘
                              │
              ┌───────────────────────────┐
              │ SERVICE STAFF MODULE       │
              ├───────────────────────────┤
              │ • Task Management         │
              │ • Service Execution       │
              │ • Time Tracking           │
              │ • Parts Tracking          │
              │ • Quality Checks          │
              │ • Report Generation       │
              │ • Work Completion         │
              │ • Payment Info Access     │
              └─────────┬─────────────────┘
                        │
           ┌────────────┼────────────┐
           │            │            │
           ▼            ▼            ▼
    ┌──────────┐  ┌──────────┐  ┌────────────┐
    │SCHEDULE  │  │SERVICE   │  │PARTS &     │
    │DATABASE  │  │EXECUTION │  │INVENTORY   │
    │          │  │DATABASE  │  │DATABASE    │
    ├──────────┤  ├──────────┤  ├────────────┤
    │• Tasks   │  │• Service │  │• Part ID   │
    │• Date/   │  │  Type    │  │• Quantity  │
    │  Time    │  │• Status  │  │• Cost      │
    │• Tech    │  │• Start   │  │• Supplier  │
    │  Assign  │  │  Time    │  │• Stock     │
    │• Vehicle │  │• End     │  │  Level     │
    │• Service │  │  Time    │  │• Usage     │
    │  Type    │  │• Issues  │  │• Reports   │
    │• Notes   │  │  Found   │  │            │
    │• Priority│  │• Parts   │  │            │
    └──────────┘  │  Used    │  └────────────┘
                  │• Labor   │
                  │  Hrs     │
                  └──────────┘
           │            │            │
           └────────────┼────────────┘
                        │
        • Work Orders
        • Service Reports
        • Time Sheets
        • Parts Usage
        • Quality Reports
        • Completion Notices
                        │
                        ▼
                   ┌──────────────┐
                   │ SERVICE STAFF│
                   │  (Dashboard) │
                   └──────────────┘
```

---

## Level 1: Inventory Staff Module Flow

```
                    ┌─────────────────┐
                    │ INVENTORY STAFF │
                    └────────┬────────┘
                             │
                    ┌─────────┴──────────────┐
                    │                        │
         • View Stock            • Manage Suppliers
         • Track Usage           • Receive Orders
         • Create Orders         • Update Pricing
                    │                        │
                    └─────────┬──────────────┘
                              │
              ┌───────────────────────────┐
              │ INVENTORY MODULE          │
              ├───────────────────────────┤
              │ • Stock Management        │
              │ • Supplier Management     │
              │ • Order Management        │
              │ • Receiving & Updates     │
              │ • Reorder Point Alerts    │
              │ • Cost Tracking           │
              │ • Usage Reports           │
              │ • Inventory Valuation     │
              └─────────┬─────────────────┘
                        │
           ┌────────────┼────────────┐
           │            │            │
           ▼            ▼            ▼
    ┌──────────┐  ┌──────────┐  ┌────────────┐
    │PARTS &   │  │SUPPLIER  │  │PURCHASE    │
    │INVENTORY │  │DATABASE  │  │ORDER       │
    │DATABASE  │  │          │  │DATABASE    │
    ├──────────┤  ├──────────┤  ├────────────┤
    │• Part ID │  │• Supplier│  │• Order ID  │
    │• Name    │  │  Name    │  │• Supplier  │
    │• Type    │  │• Contact │  │• Parts     │
    │• QTY On  │  │• Payment │  │• Quantity  │
    │  Hand    │  │  Terms   │  │• Cost      │
    │• Reorder │  │• Delivery│  │• Status    │
    │  Level   │  │  Time    │  │• Delivery  │
    │• Cost    │  │• Rating  │  │  Date      │
    │• Status  │  │• History │  │• Receipt   │
    │• Location│  │          │  │  Status    │
    └──────────┘  └──────────┘  └────────────┘
           │            │            │
           └────────────┼────────────┘
                        │
        • Stock Reports
        • Reorder Alerts
        • Supplier Orders
        • Delivery Updates
        • Cost Analysis
        • Inventory Status
                        │
                        ▼
                   ┌─────────────────┐
                   │ INVENTORY STAFF │
                   │   (Dashboard)   │
                   └─────────────────┘
```

---

## Level 1: Admin Management Module Flow

```
                    ┌─────────────────┐
                    │    ADMIN        │
                    └────────┬────────┘
                             │
                    ┌─────────┴─────────┐
                    │                   │
         • User Management      • System Configuration
         • Service Types Setup  • Reports & Analytics
         • Pricing Setup        • Audit Logs
                    │                   │
                    └─────────┬─────────┘
                              │
              ┌───────────────────────────┐
              │ ADMIN MODULE              │
              ├───────────────────────────┤
              │ • User Management         │
              │ • Role & Permission Mgmt  │
              │ • Service Setup           │
              │ • Pricing Management      │
              │ • System Configuration    │
              │ • Report Generation       │
              │ • Audit Trail Viewing     │
              │ • Alert Management        │
              │ • Backup/Recovery         │
              │ • Performance Monitoring  │
              └─────────┬─────────────────┘
                        │
           ┌────────────┼────────────────┐
           │            │                │
           ▼            ▼                ▼
    ┌──────────┐  ┌──────────┐  ┌────────────┐
    │USER      │  │SERVICE & │  │SYSTEM      │
    │DATABASE  │  │PRICING   │  │CONFIG      │
    │          │  │DATABASE  │  │DATABASE    │
    ├──────────┤  ├──────────┤  ├────────────┤
    │• User ID │  │• Service │  │• Settings  │
    │• Name    │  │  Type    │  │• Parameters│
    │• Email   │  │• Category│  │• Features  │
    │• Phone   │  │• Base    │  │• Integrat. │
    │• Role    │  │  Price   │  │• Mail      │
    │• Dept    │  │• Labor   │  │  Config    │
    │• Status  │  │  Cost    │  │• SMS       │
    │• Permiss │  │• Tax     │  │  Config    │
    │• Active  │  │• Discount│  │• Working   │
    │  Date    │  │  Rules   │  │  Hours     │
    └──────────┘  │• Duration│  │• Backup    │
                  │          │  │  Settings  │
                  └──────────┘  └────────────┘
           │            │                │
           └────────────┼────────────────┘
                        │
        • Admin Audit Logs
        • User Activity Logs
        • System Performance
        • Configuration Changes
        • Service Setup Records
        • Pricing Updates
        • Alert Notifications
                        │
                        ▼
                   ┌─────────────────┐
                   │     ADMIN       │
                   │  (Dashboard)    │
                   └─────────────────┘
```

---

## Level 2: Service Scheduling Process

```
                    ┌─────────────────┐
                    │    CUSTOMER     │
                    │(Schedule Service)│
                    └────────┬────────┘
                             │
         • Request Type    • Date/Time
         • Vehicle Select  • Notes
         • Priority Level  • Contact Info
                             │
                             ▼
              ┌──────────────────────────┐
              │ SCHEDULING ENGINE        │
              ├──────────────────────────┤
              │ • Availability Check     │
              │ • Tech Assignment        │
              │ • Cost Calculation       │
              │ • Conflict Detection     │
              │ • Confirmation Gen       │
              └────────┬─────────────────┘
                       │
    ┌──────────────────┼──────────────────┐
    │                  │                  │
    ▼                  ▼                  ▼
┌─────────────┐  ┌──────────────┐  ┌──────────────┐
│SCHEDULE     │  │TECHNICIAN    │  │COST ESTIMATE │
│DATABASE     │  │AVAILABILITY  │  │CALCULATOR    │
├─────────────┤  ├──────────────┤  ├──────────────┤
│• Service ID │  │• Tech ID     │  │• Base Price  │
│• Date       │  │• Availability│  │• Labor Cost  │
│• Time Slot  │  │• Skills      │  │• Parts Cost  │
│• Customer   │  │• Current     │  │• Taxes       │
│• Vehicle    │  │  Load        │  │• Discounts   │
│• Type       │  │• Rating      │  │• Total       │
│• Status     │  │              │  │• Payment     │
│• Tech       │  │              │  │  Options     │
│  Assigned   │  │              │  │              │
│• Cost       │  │              │  │              │
└─────────────┘  └──────────────┘  └──────────────┘
    │                  │                  │
    └──────────────────┼──────────────────┘
                       │
        • Service Booking Confirmed
        • Email/SMS Notification Sent
        • Invoice Generated
        • Appointment Set
        • Technician Notified
                       │
                       ▼
                  ┌─────────────────┐
                  │    CUSTOMER     │
                  │(Confirmation)   │
                  └─────────────────┘
```

---

## Level 2: Service Execution Process

```
                    ┌──────────────┐
                    │SERVICE STAFF │
                    │ (Start Work) │
                    └────────┬─────┘
                             │
         • Retrieve Request  • Get Vehicle
         • Verify Details    • Check Schedule
                             │
                             ▼
              ┌──────────────────────────┐
              │ SERVICE EXECUTION        │
              ├──────────────────────────┤
              │ 1. INSPECTION PHASE      │
              │    • Vehicle Assessment  │
              │    • Issue Documentation │
              │    • Photo/Video Capture │
              │                          │
              │ 2. SERVICE PHASE         │
              │    • Perform Work        │
              │    • Track Parts Usage   │
              │    • Record Labor Hours  │
              │                          │
              │ 3. QUALITY PHASE         │
              │    • Verification Checks │
              │    • Test Procedures     │
              │    • Final Approval      │
              └────────┬─────────────────┘
                       │
    ┌──────────────────┼──────────────────┐
    │                  │                  │
    ▼                  ▼                  ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│SERVICE       │  │PARTS USAGE   │  │WORK          │
│EXECUTION LOG │  │TRACKER       │  │COMPLETION    │
├──────────────┤  ├──────────────┤  ├──────────────┤
│• Service ID  │  │• Service ID  │  │• Service ID  │
│• Start Time  │  │• Part ID     │  │• End Time    │
│• End Time    │  │• Quantity    │  │• Total Hours │
│• Tech ID     │  │• Cost        │  │• Final Cost  │
│• Vehicle ID  │  │• Status      │  │• Invoice     │
│• Issues      │  │• Timestamp   │  │• Status      │
│  Found       │  │              │  │• Signature   │
│• Actions     │  │              │  │              │
│  Taken       │  │              │  │              │
│• Problems    │  │              │  │              │
│  Resolved    │  │              │  │              │
└──────────────┘  └──────────────┘  └──────────────┘
    │                  │                  │
    └──────────────────┼──────────────────┘
                       │
        • Service Report Generated
        • Invoice Created
        • Payment Processed
        • Completion Notification Sent
        • Records Updated
        • Receipt Provided
                       │
                       ▼
                  ┌──────────────┐
                  │SERVICE STAFF │
                  │(Completion)  │
                  └──────────────┘
```

---

## Level 2: Payment Processing

```
                    ┌─────────────────┐
                    │    CUSTOMER     │
                    │(Checkout Page)  │
                    └────────┬────────┘
                             │
         • Invoice Amount  • Payment Method
         • Breakdown Info  • Coupon/Discount
                             │
                             ▼
              ┌──────────────────────────┐
              │ PAYMENT PROCESSING       │
              ├──────────────────────────┤
              │ • Amount Validation      │
              │ • Coupon Application     │
              │ • Method Selection       │
              │ • Gateway Communication  │
              │ • Transaction Processing │
              │ • Receipt Generation     │
              └────────┬─────────────────┘
                       │
    ┌──────────────────┼──────────────────┐
    │                  │                  │
    ▼                  ▼                  ▼
┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│INVOICE       │  │PAYMENT       │  │TRANSACTION   │
│DATABASE      │  │GATEWAY       │  │RECORDS       │
├──────────────┤  ├──────────────┤  ├──────────────┤
│• Invoice ID  │  │• Transaction │  │• Trans ID    │
│• Amount      │  │  Details     │  │• Amount      │
│• Date        │  │• Payment     │  │• Date/Time   │
│• Customer    │  │  Response    │  │• Status      │
│• Service     │  │• Auth Code   │  │• Method      │
│• Items       │  │• Error Msgs  │  │• Reference   │
│• Tax         │  │              │  │• Confirmation│
│• Total       │  │              │  │  Code        │
│• Status      │  │              │  │              │
│• Payment     │  │              │  │              │
│  Method      │  │              │  │              │
└──────────────┘  └──────────────┘  └──────────────┘
    │                  │                  │
    └──────────────────┼──────────────────┘
                       │
        • Payment Confirmed
        • Email Receipt Sent
        • Invoice Marked PAID
        • Service Record Updated
        • Accounting Entry Created
        • Customer Notification Sent
                       │
                       ▼
                  ┌─────────────────┐
                  │    CUSTOMER     │
                  │(Receipt/Confirm)│
                  └─────────────────┘
```

---

## Data Dictionary Summary

| Module | Key Entities | Key Attributes |
|--------|--------------|-----------------|
| **Customer** | Users, Vehicles, Bookings | ID, Name, Email, Phone, Address |
| **Service Staff** | Technicians, Tasks, WorkOrders | ID, Skills, Availability, Ratings |
| **Service** | ServiceTypes, Schedules, Execution | Type, Cost, Duration, Status |
| **Inventory** | Parts, Suppliers, Orders | ID, Quantity, ReorderLevel, Cost |
| **Payment** | Invoices, Transactions, Receipts | Amount, Method, Status, Date |
| **Admin** | Users, Roles, Permissions, Config | ID, Role, Department, Status |

---

## System Integration Points

```
┌────────────────────────────────────────────────────┐
│         VEHICLE MAINTENANCE SYSTEM                 │
├────────────────────────────────────────────────────┤
│                                                    │
│  ┌──────────────┐     ┌──────────────┐           │
│  │ Payment      │────▶│ Accounting   │           │
│  │ Gateway      │     │ System       │           │
│  └──────────────┘     └──────────────┘           │
│                                                    │
│  ┌──────────────┐     ┌──────────────┐           │
│  │ SMS/Email    │────▶│ Notification │           │
│  │ Provider     │     │ System       │           │
│  └──────────────┘     └──────────────┘           │
│                                                    │
│  ┌──────────────┐     ┌──────────────┐           │
│  │ Database     │────▶│ Backup       │           │
│  │ System       │     │ Service      │           │
│  └──────────────┘     └──────────────┘           │
│                                                    │
└────────────────────────────────────────────────────┘
```

---

## Notes

- All external integrations have fallback mechanisms
- Data consistency is maintained through transaction management
- Security is enforced at all user interaction points
- Audit logs track all critical operations
- Error handling is implemented at each system boundary
- Notifications respect user preferences and time zones
