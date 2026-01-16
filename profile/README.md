# Fleetway - Comprehensive Product Overview

## Executive Summary

**Fleetway** is a comprehensive fleet management and logistics platform designed to manage commercial vehicle operations, particularly for long-haul transportation businesses. The system handles the complete lifecycle of fleet operations from booking proposals to trip execution, fuel management, financial settlements, and invoicing.

The platform is built to manage complex logistics operations involving trucks (horses), trailers, drivers, routes, and client organizations, with sophisticated features for fuel cycle management, purchase order processing, and financial reconciliation.

---

## Core Business Purpose

Fleetway serves as the central nervous system for fleet operations, enabling businesses to:

1. **Manage Fleet Assets**: Track trucks (horses), trailers, drivers, and their associations
2. **Handle Booking Operations**: Create and manage booking proposals for client shipments
3. **Execute Trips**: Plan, track, and manage trips from approval to completion
4. **Optimize Fuel Management**: Track fuel consumption, manage fuel cycles, and handle diesel purchase orders
5. **Process Financial Transactions**: Generate invoices, settlement proposals, and manage purchase orders
6. **Maintain Compliance**: Track certificates, documents, and regulatory requirements

---

## Key Modules & Features

### 1. Fleet Asset Management

#### Horses (Trucks)
- **Fleet Number Management**: Unique identification for each vehicle
- **Vehicle Details**: Engine number, chassis number, registration details
- **Fuel Type Tracking**: Diesel/Petrol classification
- **Capacity Management**: Maximum fuel capacity tracking
- **Trailer Associations**: Link horses to one or two trailers
- **Driver Associations**: Assign active drivers to vehicles
- **Status Tracking**: Vehicle status monitoring

#### Trailers
- **Identifier Management**: Unique trailer identification
- **Capacity Tracking**: Tonnage and capacity information
- **Association Management**: Link trailers to horses

#### Drivers
- **Personal Information**: Name, contact details, identification
- **Active Status**: Track active/inactive driver status
- **Horse Associations**: Link drivers to specific vehicles
- **Certificate Management**: Track driver licenses and certifications

### 2. Booking & Proposal Management

#### Booking Proposals
- **Client Management**: Create proposals for client organizations
- **Route Planning**: Associate routes with booking proposals
- **Multi-Trip Support**: Handle proposals with multiple trips
- **Rate Management**: Set rates per unit (per ton, per km, etc.)
- **Tonnage Calculation**: Automatic total tonnage calculation
- **Status Workflow**: UNAPPROVED → APPROVED status management
- **Trip Assignment**: Assign horses (fleet) to specific trips within proposals

#### Booking Proposal Trips
- **Capacity Management**: Set capacity in tons per trip
- **ETA Tracking**: Estimated time of arrival
- **Fleet Assignment**: Assign specific horses to trips
- **Metadata Support**: Flexible metadata storage for additional information
- **Status Management**: Track trip approval status within proposals

### 3. Route Management

#### Routes
- **Route Definition**: Create routes with start and destination locations
- **Stop Management**: Define multiple stops along routes
- **Stop Roles**: START, DESTINATION, and intermediate stops
- **Location Mapping**: Link stops to physical locations
- **Distance Calculation**: Total distance calculation for routes
- **Border Information**: Track exit borders for international routes
- **Route Abbreviation**: Generate abbreviated route names

#### Locations
- **Geographic Data**: Store location information
- **Route Integration**: Link locations to route stops

### 4. Trip Management

#### Trip Lifecycle
- **Trip Creation**: Automatically created when booking proposal trips are approved
- **Status Workflow**: 
  - UNAPPROVED → APPROVED → RUNNING → COMPLETED
- **Trip Identifier**: Unique identifier generation (e.g., SR002/GRB/KS/VK/2/26-01/5)
- **Route Information**: Inherit route details from booking proposal
- **Driver Assignment**: Link active driver to trip
- **Trailer Assignment**: Assign trailer1 and optional trailer2
- **Client Information**: Link to client organization
- **Distance Tracking**: Total distance for the trip
- **Estimated Days**: Estimated duration of trip

#### Trip Operations
- **Loading Point Management**: Set and update loading points
- **Route Name Updates**: Modify route information
- **Rate Management**: Update rates and rate units
- **Location Tracking**: Start and end location IDs
- **Metadata Support**: Store additional trip information

### 5. Fuel Management System

#### Horse Fuel Cycles
- **Cycle Concept**: Track fuel consumption across two trips per cycle
- **Two-Trip System**: 
  - First Trip: Outbound journey
  - Second Trip: Return journey
- **Fuel Allocation**: Allocate fuel for each trip in the cycle
- **Starting/Ending Fuel**: Track fuel levels at cycle start and end
- **Status Management**: PENDING → COMPLETED
- **Automatic Trip Assignment**: 
  - When a trip is created with RUNNING status, it's automatically assigned to the pending fuel cycle
  - First running trip becomes the first trip of the cycle
  - Second running trip becomes the second trip of the cycle
- **Fuel Consumption Calculation**: Automatic calculation based on route and vehicle type
- **Cycle Completion**: Mark cycles as completed when both trips are done

#### Diesel Purchase Orders (DPOs)
- **Purchase Order Creation**: Create DPOs for diesel purchases
- **Two Creation Modes**:
  1. **Trip-Based DPOs**: Created with trip information (trip_id)
  2. **Cycle-Based DPOs**: Created before trip is known (horse_fuel_cycle_id + part)
- **Part System**: 
  - Part 1: For first trip of fuel cycle
  - Part 2: For second trip of fuel cycle
- **Automatic Trip Assignment**: 
  - When a trip is created with RUNNING status, DPOs with matching fuel cycle and part are automatically assigned to the trip
- **Filling Station Integration**: Link to filling stations
- **Quantity & Rate Tracking**: Track quantity purchased and rate per unit
- **Currency Support**: Multi-currency support
- **State Management**: PENDING_APPROVAL → APPROVED → UNAPPROVED
- **Receipt Management**: Store driver and station receipt paths
- **Filtering**: Filter DPOs by trip, horse, fuel cycle, filling station

#### Fuel Consumption
- **Consumption Records**: Store fuel consumption data by vehicle brand, route, and tonnage
- **Calculation Logic**: Calculate fuel needed based on:
  - Vehicle brand
  - Start and end locations
  - Tonnage
- **Route-Based Calculation**: Use route information to determine fuel requirements

### 6. Purchase Order Management

#### Diesel Purchase Orders
- **Order Numbering**: Unique purchase order numbers
- **Supplier Management**: Track supplier names
- **Filling Station Integration**: Link to filling stations
- **Trip Association**: Link to trips (can be null initially)
- **Fuel Cycle Association**: Link to horse fuel cycles
- **Part Tracking**: Track which part of fuel cycle (1 or 2)
- **Quantity & Pricing**: Track quantity, rate, and currency
- **State Workflow**: PENDING_APPROVAL → APPROVED → UNAPPROVED
- **Receipt Storage**: Store driver and station receipts
- **User Tracking**: Track which user created the order

#### Security Purchase Orders
- **Security Services**: Purchase orders for security services at borders
- **Trip Association**: Link to specific trips
- **Border Information**: Track border locations
- **Amount Tracking**: Track security service costs

#### Filling Stations
- **Station Management**: Manage filling station information
- **Station Names**: Track station names
- **DPO Integration**: Link to diesel purchase orders

### 7. Financial Management

#### Invoices
- **Invoice Generation**: Create invoices for trips
- **Invoice Types**: 
  - LOADING: For loading operations
  - UNLOADING: For unloading operations
- **Trip Association**: Link invoices to trips
- **Client Organization**: Link to client organizations
- **Document Storage**: Store invoice documents
- **Status Tracking**: Track invoice status

#### Settlement Proposals
- **Order Management**: Create settlement proposals with order numbers
- **Vendor Management**: Track vendor IDs and details
- **Reference Numbers**: Link to reference documents
- **Percentage Tracking**: Track percentage-based settlements
- **Document Storage**: Store settlement proposal documents
- **Trip Expense Details**: Link to trip client expense details
- **Type Classification**: LOADING or UNLOADING settlement proposals

#### Trip Client Expense Details
- **Expense Tracking**: Track client expenses per trip
- **Invoice Type**: Link to invoice types
- **Settlement Proposal Link**: Link to settlement proposals
- **Quantity & Pricing**: Track quantity, unit, price per unit
- **Total Calculation**: Calculate total excluding tax
- **Type Classification**: LOADING or UNLOADING expenses

### 8. Certificate & Document Management

#### Certificates
- **Entity Types**: 
  - TRAILER
  - HORSE
  - DRIVER
  - BOOKING_PROPOSAL_TRIP
  - FINANCE
- **Certificate Types**: Various certificate types per entity
- **Document Storage**: Store certificate documents
- **Expiry Tracking**: Track issue and expiry dates
- **Status Management**: Track certificate status
- **Issuing Authority**: Track issuing authority and country

### 9. Client & Organization Management

#### Client Organizations
- **Organization Management**: Manage client organization details
- **Contact Information**: Email, phone, address
- **Booking Proposal Integration**: Link to booking proposals
- **Invoice Integration**: Link to invoices

#### Teams & Users
- **Team Management**: Organize users into teams
- **User Roles**: Role-based access control
- **Permission System**: Fine-grained permission management
- **Organization Membership**: Users belong to organizations

### 10. Authentication & Authorization

#### Authentication
- **Auth0 Integration**: OAuth2 authentication via Auth0
- **JWT Tokens**: Bearer token authentication for API
- **Organization-Based Login**: Support for organization-specific logins
- **Session Management**: Browser-based sessions for web access

#### Authorization
- **Permission-Based Access**: Fine-grained permission checking
- **Role-Based Access**: Role-based access control
- **API Security**: Stateless API authentication
- **Web Security**: Session-based web authentication

---

## Key Business Workflows

### 1. Complete Trip Lifecycle

```
1. Create Booking Proposal
   ↓
2. Add Booking Proposal Trips (with horse assignment)
   ↓
3. Approve Booking Proposal Trip
   ↓
4. System automatically creates Trip with RUNNING status
   ↓
5. Trip is assigned to pending Horse Fuel Cycle
   ↓
6. Diesel Purchase Orders can be created (with or without trip)
   ↓
7. DPOs are automatically assigned to trips when trips become RUNNING
   ↓
8. Trip status updated to COMPLETED
   ↓
9. Fuel cycle can be marked as COMPLETED
   ↓
10. Generate invoices for the trip
   ↓
11. Create settlement proposals
```

### 2. Fuel Cycle Management Workflow

```
1. System detects running trip for a horse
   ↓
2. Creates pending Horse Fuel Cycle (if none exists)
   ↓
3. First running trip → assigned as firstTrip of cycle
   ↓
4. Diesel Purchase Orders can be created:
   - With trip_id (if trip exists)
   - With horse_fuel_cycle_id + part (if trip doesn't exist yet)
   ↓
5. Second running trip → assigned as secondTrip of cycle
   ↓
6. DPOs with matching cycle and part are auto-assigned to trips
   ↓
7. Fuel consumption calculated for both trips
   ↓
8. Cycle marked as COMPLETED
```

### 3. Purchase Order Workflow

```
1. Create Diesel Purchase Order
   - Option A: With trip_id (trip already exists)
   - Option B: With horse_fuel_cycle_id + part (trip not yet created)
   ↓
2. If Option B: DPO stored with trip_id = null
   ↓
3. When trip is created with RUNNING status:
   - System finds DPOs for that fuel cycle and part
   - Automatically assigns trip to those DPOs
   ↓
4. DPO state: PENDING_APPROVAL → APPROVED
   ↓
5. Receipts uploaded (driver receipt, station receipt)
```

### 4. Financial Workflow

```
1. Trip completed
   ↓
2. Create Invoice (LOADING or UNLOADING)
   ↓
3. Create Trip Client Expense Details
   ↓
4. Create Settlement Proposal
   ↓
5. Link Settlement Proposal to Trip Client Expense Details
   ↓
6. Generate documents and store paths
```

---

## Key Entities & Relationships

### Core Entities

1. **Horse (Truck)**
   - Has: Trailers (1-2), Drivers (active), Fuel Cycles
   - Belongs to: Organization

2. **Trip**
   - Has: Driver, Trailers, Booking Proposal Trip, Route Info
   - Belongs to: Horse (via fleetId), Client Organization
   - Related to: Fuel Cycles, Purchase Orders, Invoices

3. **Horse Fuel Cycle**
   - Has: First Trip, Second Trip, Fuel Allocations
   - Belongs to: Horse
   - Related to: Diesel Purchase Orders

4. **Diesel Purchase Order**
   - Belongs to: Trip (optional), Horse, Horse Fuel Cycle (optional)
   - Related to: Filling Station

5. **Booking Proposal**
   - Has: Booking Proposal Trips, Client Organization
   - Related to: Route

6. **Booking Proposal Trip**
   - Belongs to: Booking Proposal
   - Creates: Trip (when approved)

7. **Invoice**
   - Belongs to: Trip, Client Organization
   - Type: LOADING or UNLOADING

8. **Settlement Proposal**
   - Related to: Trip Client Expense Details

---

## Technical Architecture Highlights

### Technology Stack
- **Backend**: Spring Boot (Kotlin)
- **Database**: PostgreSQL
- **Authentication**: Auth0 (OAuth2, JWT)
- **File Storage**: Supabase Storage
- **API**: RESTful API with OpenAPI/Swagger documentation

### Key Design Patterns
- **Layered Architecture**: Controller → Application → Domain → Repository
- **Domain-Driven Design**: Business logic in domain layer
- **Repository Pattern**: Data access abstraction
- **Specification Pattern**: Dynamic query building
- **Action Pattern**: Application layer actions for business operations

### Data Flow
1. **API Request** → Controller
2. **Controller** → Application Action
3. **Application Action** → Domain Logic (if needed)
4. **Application Action** → Repository Action
5. **Repository Action** → Database
6. **Response** flows back through layers

---

## Business Value & Benefits

### Operational Efficiency
- **Automated Trip Management**: Reduces manual data entry
- **Fuel Cycle Optimization**: Tracks fuel consumption across round trips
- **Purchase Order Automation**: Auto-assigns DPOs to trips when trips are created
- **Route Optimization**: Tracks routes and distances for planning

### Financial Control
- **Invoice Management**: Streamlined invoice generation
- **Settlement Tracking**: Clear settlement proposal management
- **Purchase Order Tracking**: Complete audit trail of fuel purchases
- **Multi-Currency Support**: Handle international operations

### Compliance & Documentation
- **Certificate Management**: Track all required certificates
- **Document Storage**: Centralized document management
- **Receipt Management**: Store and track purchase receipts
- **Audit Trail**: Complete history of all operations

### Scalability
- **Multi-Organization Support**: Handle multiple organizations
- **Team Management**: Organize users into teams
- **Permission System**: Fine-grained access control
- **Flexible Metadata**: Store additional information as needed

---

## Key Differentiators

1. **Intelligent Fuel Cycle Management**: 
   - Automatically tracks fuel consumption across two-trip cycles
   - Handles DPOs created before trips are known
   - Auto-assigns DPOs to trips when trips become active

2. **Flexible Purchase Order System**:
   - Support for trip-based and cycle-based DPOs
   - Automatic trip assignment when trips are created
   - Part-based tracking for fuel cycle phases

3. **Comprehensive Trip Management**:
   - Automatic trip creation from booking proposals
   - Status workflow from approval to completion
   - Integration with fuel cycles and purchase orders

4. **Financial Integration**:
   - Seamless invoice generation
   - Settlement proposal management
   - Expense detail tracking

---

## Future Considerations

The system is designed to be extensible and can accommodate:
- Additional vehicle types
- More complex route planning
- Advanced analytics and reporting
- Integration with external systems (GPS tracking, accounting systems)
- Mobile applications for drivers
- Real-time tracking and notifications

---

## Conclusion

Fleetway is a comprehensive, enterprise-grade fleet management platform that handles the complete lifecycle of fleet operations. From asset management to trip execution, fuel optimization to financial reconciliation, the system provides a unified platform for managing complex logistics operations with automation, intelligence, and compliance built-in.

The system's intelligent fuel cycle management and flexible purchase order system make it particularly well-suited for long-haul transportation businesses that need to optimize fuel consumption and manage complex trip schedules across multiple vehicles, drivers, and routes.
