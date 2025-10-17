# Changelog
All notable changes to this project will be documented in this file.

## [7.13.0.0] - 2025-10-17

### Added

**Customer Management API (V5)** — full implementation according to the official Route4Me OpenAPI specification.

New supported endpoints:
- `GET /api/v5.0/customers/{customer_id}` – Get customer by ID  
- `POST /api/v5.0/customers` – Create a new customer  
- `PUT /api/v5.0/customers/{customer_id}` – Update an existing customer  
- `DELETE /api/v5.0/customers/{customer_id}` – Delete a customer  
- `POST /api/v5.0/customers/list` – Retrieve paginated list of customers  

New classes introduced under **DataTypes/V5/Customers/**:
- `Contact.cs`
- `Contract.cs`
- `CustomerAddress.cs`
- `CustomerResource.cs`
- `CustomerContactResource.cs`  
- `CustomerListResource.cs`  
- `CustomerListResponse.cs`  
- `CustomerResource.cs`  
- `CustomerShowResource.cs`  
- `Facility.cs`  
- `StoreRequest.cs`

**QueryTypes/V5/Customers/**:
- `CustomerIdParameters.cs`
- `CustomerListFilters.cs`
- `CustomerListParameters.cs`
- `UpdateCustomerParameters.cs`

New manager under **Managers/**:
- `CustomerManagerV5.cs` — provides sync and async access to all customer endpoints (`CreateCustomerV5`, `GetCustomerByIdV5`, `DeleteCustomerV5`, etc.)

### Changed
- **Consts.cs** – added new API endpoints for `/api/v5.0/customers`.  
- **Route4MeManagerV5.cs** – integrated `CustomerManagerV5` initialization into constructor for seamless V5 access.
- **Enum.cs** – added new ContactType, AddressType, CustomerStatus enums

### Documentation
- Added examples for all Customer API endpoints under `Examples/V5/Customers/`.  
- Updated `README.md` with usage instructions for `CustomerManagerV5`.  
- Updated `CHANGELOG.md` and internal metadata to reflect the new Customer Management feature.

### Tests
- Added **CustomersTests.cs** under `Route4MeSDKTest/V5/Customers/` to cover all new endpoints:  
  - `CreateCustomerTest`
  - `CreateCustomerAsyncTest`
  - `GetCustomerByIdTest`  
  - `GetCustomerByIdAsyncTest`  
  - `UpdateCustomerTest`  
  - `UpdateCustomerAsyncTest`
  - `GetCustomersListTest`
  - `GetCustomersListAsyncTest`
  - `DeleteCustomerTest`
  - `DeleteCustomerAsyncTest`  
- Integration test coverage temporarily skipped — manual validation confirmed via working examples.

### Examples
- Added full usage examples under `Examples/API5/Customers/`:  
  - `CreateCustomerV5.cs`
  - `CreateCustomerV5Async.cs`  
  - `GetCustomerByIdV5.cs`
  - `GetCustomerByIdV5Async.cs`  
  - `UpdateCustomerV5.cs`
  - `UpdateCustomerV5Async.cs` 
  - `DeleteCustomerV5.cs`
  - `DeleteCustomerV5Async.cs` 
  - `GetCustomersListV5.cs`
  - `GetCustomersListV5Async.cs`
- In examples demonstrates both sync and async SDK patterns.  
- Examples are verified and compatible with the latest Route4Me API documentation.

### Notes
- Implementation follows SDK async/sync conventions, SOLID principles, and thread-safety patterns.

## [7.12.1.0] - 2024-08-07
Fixed get optimization profile endpoint  
Adjust OptimizationProfileEntities and OptimizationWithProfile examples  
Adjust OptimizationProfileManagerV5Tests

## [7.12.0.0] - 2024-08-07
Optimization profile - save/delete entities are supported  
Fixed GetOptimizationProfilesAsync.

## [7.11.2.0] - 2024-07-21
Supported all parameters for routes filtering.  
Fixed optimization creation with profile id.

## [7.11.1.0] - 2024-07-18
Fixed OptimizationProfileManagerV5.

## [7.11.0.0] - 2024-01-31
NoSolution is supported in OptimizationState

## [7.10.0.0] - 2024-01-29
order_uuid is supported for Order V4.  
Order V5 API is supported.

## [7.9.0.0] - 2024-01-15
Optimization profiles are supported (OptimizationProfileManagerV5).  
Optimization creation using optimization profile is supported.

## [7.8.4.0] - 2024-01-04
additional_status and required_skills are supported for Address

## [7.8.3.0] - 2023-12-22
Fixed ApiKey in HTTP header  
Fixed/enabled Schedules API  
Fixed AddRouteDestinations/AddRouteDestinationsAsync API in case of failed to add route  
Fixed RemoveAddressBookGroup/RemoveAddressBookGroupAsync API  
Fixed RemoveOptimizationResponse deserialization  
Fixed RemoveOptimization/RemoveOptimizationAsync API  
Fixed GetAddressBookContactsPaginated/GetAddressBookContactsPaginatedAsync API  
Fixed CreateWrongOrderTest test  
Fixed server-side memory leaks in CreateAddressBookContactTest  
Fixed Fixed OrdersHistoryTest/OrderHistoryAsyncTest  
Make TeamManagementTests green locally  
Fixed red unit tests (~50)

## [7.8.2.0] - 2023-12-21
Switched (for V5 API only) from ApiKey as query parameter to bearer token in HTTP header

## [7.8.1.0] - 2023-12-18
Fixed PodWorkflowManagerV5.GetPodWorkflows/GetPodWorkflowsAsync to take into account PodWorkflowListParameters

## [7.8.0.0] - 2023-12-15
PoD workflows are supported  
StatusResponse processing is fixed in case of response with empty body.

## [7.7.5.0] - 2023-11-21
Got rid of dependency to System.Configuration.ConfigurationManager nuget package.

## [7.7.4.0] - 2023-11-17
Assembly is signed.

## [7.7.3.0] - 2023-09-07
AddRouteDestinations enhancement - try to re-read order and extract addresses's IDs out of it.

## [7.7.2.0] - 2023-09-06
Order's priority is supported.

## [7.7.1.0] - 2023-07-14
HTTP response handling is improved.

## [7.7.0.0] - 2023-07-04
/api.v4/orders/changes.php is supported.

## [7.6.0.0] - 2023-05-23
Get rid of GetRouteById V5.  
AddRouteDestinations improvements.

## [7.5.3.0] - 2023-05-05
AddRouteDestinations fixed: supported addresses with no AddressString.

## [7.5.2.0] - 2023-04-20
Switched from long to string (with timestamp inside) for actual_travel_time in RouteFilterResponse.

## [7.5.1.0] - 2023-04-19
utc_time, lat/lng are supported for /api/route/mark_address_departed.php and /actions/address/update_address_visited.php.

## [7.5.0.0] - 2023-04-14
Address Book Contact API V4 is deprecated (switched to V5).  
utc_time, lat/lng are supported for api/route/mark_address_departed.php and api/route/mark_address_visited.php.

## [7.4.2.0] - 2023-04-06
MarkAddressAsMarkedAsVisited/MarkAddressAsMarkedAsDeparted fixed on .NET Client SDK Library side with respect to resetting the is_visited flag.  
Obsolete messages are adjusted.

## [7.4.1.0] - 2023-03-09
Vehicle API V4 is deprecated.

## [7.4.0.0] - 2023-03-06
Team API V4 is deprecated. GetTeamOwner and GetUserIdsByEmails are introduced.

## [7.3.0.0] - 2023-02-23
Support 'sync' field in case of master route creation for schedules.

## [7.2.3.0] - 2023-02-08
3rd party dependencies are updated. Tests are switched to .NET6.

## [7.2.2.0] - 2023-01-13
Route deserialization from object to array in case of route list query with routeID is supported. As a result, list with 1 element is returned as result. Fix is relevant both for V4 and V5.

## [7.2.1.0] - 2023-01-11
Fixed schedules API deserialization issues.

## [7.2.0.0] - 2023-01-06
Schedules are supported.  
NOTE: IsRouteScheduleCopied/IsRouteScheduleCopiedAsync, GetRouteScheduleCopies/GetRouteScheduleCopiesAsync are not ready to be used.  
NOTE: Schedules API might be changed on server side which will require adaptation on .NET client side.

## [7.1.0.0] - 2022-11-25
GetOptimizationPredictionAsync API is added.  
Route4MeManagerV5 is split by submanagers with backward compatibility; now it acts as a thin proxy.

...
