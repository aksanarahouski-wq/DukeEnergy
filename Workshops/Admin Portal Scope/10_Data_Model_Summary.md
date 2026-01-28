# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---

## DATA MODEL SUMMARY

### Core Admin Entities:

**1. AdminUser**
- admin_user_id (PK)
- username
- email
- role (CSR, BackOffice, ProductManager, OperationsManager, Analyst, SuperAdmin)
- permissions (JSON or role-based)
- created_date
- last_login

**2. Customer (Aggregated from CRM + App)**
- customer_id (PK)
- customer_type (duke_native, pg_native, non_native)
- source_system (commerce, dynamics, app)
- utility_account_number (null if non-native)
- first_name, last_name
- email, phone
- address (street, city, state, zip)
- loyalty_points
- profile_completion_percentage
- created_date, last_login

**3. HomeInventory**
- inventory_id (PK)
- customer_id (FK)
- item_type (HVAC, WaterHeater, Appliance, etc.)
- category (tankless, tanked, central_ac, heat_pump, etc.)
- make, model, serial_number
- installation_date, age
- warranty_expiration
- location_in_home
- added_by (customer, admin, contractor)
- created_date, updated_date

**4. ServiceRequest**
- service_request_id (PK)
- customer_id (FK)
- service_type (hpp_covered, ad_hoc)
- service_category (HVAC, plumbing, electrical, etc.)
- problem_description
- inventory_item_id (FK, optional)
- contractor_id (FK)
- scheduled_date, scheduled_time_window
- status (requested, assigned, en_route, on_site, completed, cancelled)
- payment_status
- customer_rating
- source_system (app, phone, crm)
- created_date, updated_date

**5. AdHocService**
- service_id (PK)
- service_name
- service_code_sku
- category
- description
- scope_of_work (text)
- pricing_type (fixed, variable, quote)
- base_price
- regional_price_overrides (JSON)
- geographic_availability (zip_codes or regions)
- status (draft, active, inactive)
- created_by (admin_user_id)
- created_date, updated_date

**6. Reminder**
- reminder_id (PK)
- title
- description
- frequency (monthly, quarterly, biannually, annually, seasonal)
- asset_category (FK)
- optional_service_link (FK to AdHocService)
- optional_hpp_plan_link (FK)
- status (active, inactive)
- created_by (admin_user_id)
- created_date, updated_date

**7. EnrollmentQueue**
- queue_item_id (PK)
- customer_id (FK)
- enrollment_details (JSON)
- status (pending, in_progress, processed, failed)
- assigned_to (admin_user_id)
- created_date, processed_date

**8. EscalationTicket**
- ticket_id (PK)
- customer_id (FK)
- service_request_id (FK, optional)
- issue_category
- issue_description
- priority (low, medium, high, urgent)
- status (open, in_progress, resolved, closed)
- assigned_to (admin_user_id)
- resolution_notes
- created_date, resolved_date

---

**Document Owner:** Orases Product Management Team
**Last Updated:** November 19, 2025
**Status:** Ready for wireframe creation

---

**Related Documents:**
- [Customer App Preliminary Scope & Flows](Customer_App_Preliminary_Scope_and_Flows.md)
- [Session 1: Customer Discovery](Session_1_Customer_Discovery.md)
- [Session 2: Admin Discovery](Session_2_Admin_Discovery.md)
- [Session 3: Contractor Discovery](Session_3_Contractor_Discovery.md) - TO BE COMPLETED
- [HPP Plans Explained](HPP_Plans_Explained.md)
- [P&G Customer References](P&G_Customer_References.md)
