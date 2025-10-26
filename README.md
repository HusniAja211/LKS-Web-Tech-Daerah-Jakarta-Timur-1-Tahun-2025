```markdown
# LKS JAKARTA JT 1 2025

## SERVER SIDE MODULE PART I (REST API & AUTHORIZATION)

### [cite_start]CONTENTS [cite: 4]

[cite_start]This module has the following files[cite: 5]:
1.  [cite_start]`MODULE_SERVER_SIDE_JT1_25.docx` [cite: 6]
2.  [cite_start]`MODULE_SERVER_SIDE_JT1_25.pdf` [cite: 7]
3.  [cite_start]`MODULE_SERVER_SIDE_MEDIA.zip` [cite: 7]

### [cite_start]INTRODUCTION [cite: 8]

[cite_start]PrOECCECL [cite: 9]
[cite_start]`$table` [cite: 10]
[cite_start]`= 'nama_table'` [cite: 11]

[cite_start]In this module, you are asked to create a minimum viable product healthcare application for the specification of the doctor scheduling system[cite: 12]. [cite_start]The detailed description and tools that you can use will be described below[cite: 13].

### [cite_start]DESCRIPTION OF PROJECT AND TASKS [cite: 14]

[cite_start]This module is divided into 2 phases[cite: 15]. [cite_start]In the first phase, you will create a REST Api using Authentification then in the second phase you will create a frontend application with the following provided frameworks[cite: 15]:

* [cite_start]**Laravel** (v11.x) [cite: 16]
* [cite_start]**React** (v18.^ with react-router and axios module) [cite: 18]
* [cite_start]**Vue** (v3.^ with vue-router and axios module) [cite: 20]

---

## [cite_start]Phase 1 REST API & Authentication [cite: 21]

[cite_start]For all endpoints, the request header as default sets `Content-type: application/json`, but some endpoints have specified `Content-type` header so you have to adjust it[cite: 22].

### [cite_start]1. Authentication [cite: 23]

[cite_start]You can use **sanctum** for the token management and it must be valid when placed in the `Authorization` request header as a **Bearer token**[cite: 24].

#### a. [cite_start]Login [cite: 25]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/auth/login` [cite: 26] | [cite_start]`POST` [cite: 26] | [cite_start]For user to log into system [cite: 26] |

| Request | Response Success | Response Failed |
| :--- | :--- | :--- |
| [cite_start]**Body:** `username`, `password` [cite: 29] | [cite_start]**HTTP Status Code:** 200 [cite: 29][cite_start], **Body:** `{"message": "Login success", "token": "2|Qnt2aqHIi0EVwCz3rSH0yiFIKMqey38SdkUZntRvf0e507ff", "user": {"user id": 1, "user full name": "Budiman", "user username": "Admin", "created_at": "2023-10-14T15:04:33.000000%"}}` [cite: 29] | [cite_start]**HTTP Status Code:** 401 [cite: 29][cite_start], **Body:** `{"message": "username or password are incorrect"}` [cite: 29]

#### b. [cite_start]Logout [cite: 30]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/auth/logout` [cite: 31] | [cite_start]`POST` [cite: 31] [cite_start]| user to logout [cite: 31] |

| Request | Response Success | Response Invalid Token |
| :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 31][cite_start], **Body:** `username`, `password` [cite: 31] | [cite_start]**HTTP Status Code:** 200 [cite: 31][cite_start], **Body:** `{"message": "Logout success"}` [cite: 31] | [cite_start]**HTTP Status Code:** 401 [cite: 31][cite_start], **Body:** `{ "message": "Unauthenticated."` [cite: 31]

### [cite_start]2. Poliklinik [cite: 32]

#### a. [cite_start]Create Poliklinik [cite: 33]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/poliklinik` [cite: 34] | [cite_start]`POST` [cite: 34] | [cite_start]Admin can create a Poliklinik [cite: 34] |

| Request | Response Success | Response Invalid Field | Response Invalid Token |
| :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 37][cite_start], **Body:** `Poliklinik ID` (string; maxlength:10; required), `Name` (string; required), `Description` (string; optional) [cite: 37] | [cite_start]**HTTP Status Code:** 200 [cite: 37][cite_start], **Body:** `"message": "Poliklinik is created"` [cite: 37] | [cite_start]**Body Status Code:** 422[cite: 37], **Body:** `{"message": "Invalid field", "errors": {"PoliklinikID": ["Poliklinik ID field is required." 1, "name": ["Poliklinik Name field is required." [cite_start]1}}` [cite: 37] | [cite_start]**HTTP Status Code:** 401 [cite: 37][cite_start], **Body:** `ini gimana caranya "message": "Unauthenticated."` [cite: 37]

#### b. [cite_start]Update Poliklinik [cite: 38]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/Poliklinik/:id` [cite: 39] | [cite_start]`PUT` [cite: 39] | [cite_start]Admin can update the Poliklinik by id. [cite: 39] |

| Request | Response Success | Response Invalid Field | Response Not Found | Response Invalid Token |
| :--- | :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 39][cite_start], **Body:** `Name` (string; required), `Description` (string; optional) [cite: 39] | [cite_start]**HTTP Status Code:** 200 [cite: 39][cite_start], **Body:** `{"message": "Poliklinik modified"}` [cite: 39] | [cite_start]**Body Status Code:** 422[cite: 43], **Body:** `"message": "Invalid field", "errors": {"name": ["Poliklinik Name field is required." [cite_start]1}` [cite: 44, 45, 46, 47, 48] | [cite_start]**HTTP Status Code:** 404 [cite: 53][cite_start], **Body:** `"message": "Poliklinik not found"` [cite: 55] | [cite_start]**HTTP Status Code:** 401 [cite: 57][cite_start], **Body:** `"message": "Unauthenticated."` [cite: 61]

#### c. [cite_start]Delete Poliklinik [cite: 62]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/Poliklinik/:id` [cite: 63] | [cite_start]`DELETE` [cite: 63] | [cite_start]Admin can delete the Poliklinik if there is no schedule attached [cite: 63] |

| Request | Response Success | Response Constraint Error | Response Not Found | Response Invalid Token |
| :--- | :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 63] | [cite_start]**HTTP Status Code:** 204 [cite: 63] | [cite_start]**HTTP Status Code:** 422 [cite: 63][cite_start], **Body:** `T "message": "Poliklinik cannot deleted"` [cite: 63] | [cite_start]**HTTP Status Code:** 404 [cite: 63][cite_start], **Body:** `{ "message": "Poliklinik not found"` [cite: 63] | [cite_start]**HTTP Status Code:** 401 [cite: 63][cite_start], **Body:** `"message": "Unauthenticated."` [cite: 63]

#### d. [cite_start]Get All Poliklinik [cite: 64]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/Poliklinik` [cite: 65] | [cite_start]`GET` [cite: 65] | [cite_start]Admin to get all Poliklinik data [cite: 65] |

| Request | Response Success | Response Invalid Params | Response Invalid Token |
| :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 65][cite_start], **Params:** `page` (integer, minimum 0 and default 0), `size` (integer, minimum 1 and default 10) [cite: 69] | [cite_start]**HTTP Status Code:** 200 [cite: 69][cite_start], **Body:** `{"page": 0, "size": 10, "Polikliniks": [{"PoliklinikID": "KD01", "PoliklinikName": "Poli Gigi", "PoliklinikDesc": "", "createdAt": "2025-01-20 00:34:10", "updatedAt": null, "schedules": {"id": 61, "doctorName": "Irving Greenfelder", "scheduleDate": "2025-01-30", "startTime": "10:00", "endTime": "12:00", "created at": "2025-01-20 19:16:53"}}]}` [cite: 69] | [cite_start]**HTTP Status Code:** 422[cite: 69], **Body:** `{"message": "Invalid field", "errors": {"page": ["The page field must be at least 0." 1, "size": ["The size field must be a number." [cite_start]1}}` [cite: 69] | [cite_start]**HTTP Status Code:** 401 [cite: 69][cite_start], **Body:** `1 "message": "Unauthenticated."` [cite: 69]

### [cite_start]3. Doctor [cite: 70]

#### a. [cite_start]Create Doctor [cite: 71]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/doctor` [cite: 72] | [cite_start]`POST` [cite: 72] | [cite_start]Admin to create a doctor [cite: 72] |

| Request | Response Success | Response Invalid Field | Response Invalid Token |
| :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 72][cite_start], **Body:** `Doctor ID` (string; maxlength: 15; required), `Name` (string, required), `Gender` (male/female /required) [cite: 75][cite_start], `Phone Number` (string; required), `Address` (string; required), `Email` (string; required), `Bio` (string optional) [cite: 75] | [cite_start]**HTTP Status Code:** 200 [cite: 75][cite_start], **Body:** `{"message": "Doctor created"}` [cite: 75] | [cite_start]**Body Status Code:** 422[cite: 75], **Body:** `{"message": "Invalid field", "errors": {"doctorID": ["Doctor ID field is required." 1], "name": ["Name field is required." 1], "gender": ["Gender field is required. and must be For M" 1], "phone": ["Phone field is required." 1], "address": ["Address field is required." 1], "email": ["Email field is required." [cite_start]1}}` [cite: 75] | [cite_start]**HTTP Status Code:** 401 [cite: 75][cite_start], **Body:** `1 "message": "Unauthenticated."` [cite: 75]

#### b. [cite_start]Update Doctor [cite: 76]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/doctor/:id` [cite: 77] | [cite_start]`PUT` [cite: 79] | [cite_start]Admin can update existing doctors by id. [cite: 80] |

| Request | Response Success | Response Invalid Field | Response Not Found | Response Invalid Token |
| :--- | :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 82][cite_start], **Body:** `Name` (string; required), `Gender` (male/female; required), `Phone Number` (string; required), `Address` (string; required), `Email` (string; required), `Bio` (string; optional) [cite: 84, 85, 86, 87, 88] | [cite_start]**HTTP Status Code:** 200 [cite: 92][cite_start], **Body:** `"message": "Doctor modified"` [cite: 94] | [cite_start]**Body Status Code:** 422[cite: 101], **Body:** `"message": "Invalid field", "errors": {"name": [1, "Name field is required." 106], "gender": ["Gender field is required. I and must be For M" 1], "phone": [1, "Phone field is required." 1], "address": ["Address field is required." 1], "email": ["Email field is required." [cite_start]1}}` [cite: 102, 103, 104, 105, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 117, 118] | [cite_start]**HTTP Status Code:** 404 [cite: 119][cite_start], **Body:** `"message": "Doctor not found"` [cite: 121] | [cite_start]**HTTP Status Code:** 401 [cite: 122][cite_start], **Body:** `{ "message": "Unauthenticated."` [cite: 125]

#### c. [cite_start]Delete Doctor [cite: 126]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/doctor/:id` [cite: 127] | [cite_start]`DELETE` [cite: 127] | [cite_start]Admin can delete doctor transaction if there is no schedule attached [cite: 127] |

| Request | Response Success | Response Constraint Error | Response Not Found | Response Invalid Token |
| :--- | :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 127] | [cite_start]**HTTP Status Code:** 204 [cite: 127] | [cite_start]**HTTP Status Code:** 422 [cite: 127][cite_start], **Body:** `{ "message": "Doctor cannot deleted"` [cite: 127] | [cite_start]**HTTP Status Code:** 404 [cite: 127][cite_start], **Body:** `"message": "Doctor not found"` [cite: 134] | [cite_start]**HTTP Status Code:** 401 [cite: 136][cite_start], **Body:** `"message": "Unauthenticated."` [cite: 140]

#### d. [cite_start]Get All Doctors [cite: 141]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/doctor` [cite: 143] | [cite_start]`GET` [cite: 145] | [cite_start]Admin to get all doctor data [cite: 146] |

| Request | Response Success | Response Invalid Params | Response Invalid Token |
| :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 149][cite_start], **Params:** `page` (integer, minimum 0 and default 0), `size` (integer, minimum 1 and default 10) [cite: 152] | [cite_start]**HTTP Status Code:** 200 [cite: 153][cite_start], **Body:** `[1, "page": 0, "size": 10, "doctors": [{"doctorID": "DOC001", "doctorName": "Fulan", "gender": " ", "phone": "08881288", "address": "Jl. Sepanjang Kenangan", "email": "fulan@gmail.com", "bio": "", "createdAt": "2025-01-20 00:34:10", "updatedAt": null, "schedules": {"Id": 61, "PoliklinikName": "Poli Umum", "scheduleDate": "2025-01-30", "startTime": "09:00", "endTime": "15:00", "created at": "2025-01-20 19:16:53"}}]` [cite: 154, 155, 156, 157, 158, 159, 160, 161, 162, 163, 164, 165, 166, 167, 168, 169, 170, 171, 172, 173, 174, 175, 176, 177] | [cite_start]**HTTP Status Code:** 422[cite: 178], **Body:** `"message": "Invalid field", "errors": {"page": ["The page field must be at least 0." 1], "size": ["The size field must be a number." [cite_start]1}}` [cite: 182, 183, 184, 185, 186, 187, 189] | [cite_start]**HTTP Status Code:** 401 [cite: 190][cite_start], **Body:** `1 "message": "Unauthenticated."` [cite: 190]

### [cite_start]4. Schedule [cite: 191]

#### a. [cite_start]Create Schedule [cite: 192]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/schedule` [cite: 193] | [cite_start]`POST` [cite: 193] | Admin to create a schedule. [cite_start]Make sure that there is no conflicting schedule (1 doctor with 2 schedules with conflicting hours). [cite: 193] |

| Request | Response Success | Response Invalid Field | Response Invalid Token |
| :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 193][cite_start], **Body:** `Doctor ID` (string; maxlength: 15; required), `Poliklinik ID` (string; maxlength: 10; required), `Date` (date; min:tomorrow; required), `Start Time` (time; required), `End Time` (time; required) [cite: 193] | [cite_start]**HTTP Status Code:** 200 [cite: 193][cite_start], **Body:** `"message": "Schedule created"` [cite: 193] | [cite_start]**Body Status Code:** 422[cite: 193], **Body:** `{"message": "Invalid field", "errors": {"doctorID": ["Doctor field is required." 1], "PoliklinikID": ["Poliklinik field is required." 1], "date": ["Date field is required. Minimal tomorrow" 1], "startTime": ["Start Time field is required." 1], "endTime": ["End Time field is required." [cite_start]1]}}` [cite: 193] | [cite_start]**HTTP Status Code:** 401 [cite: 193][cite_start], **Body:** `( "message": "Unauthenticated."` [cite: 194, 196]

#### b. [cite_start]Update Schedule [cite: 197]

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| [cite_start]`/api/v3/schedule/:id` [cite: 198] | [cite_start]`PUT` [cite: 198] | Admin can update existing schedules by id. [cite_start]The schedule cannot be changed once the date has passed the current date. [cite: 198] |

| Request | Response Success | Response Invalid Field | Response Not Found | Response Invalid Token |
| :--- | :--- | :--- | :--- | :--- |
| [cite_start]**Headers:** `Authorization: Bearer <token>` [cite: 198][cite_start], **Body:** `Doctor ID` (string; maxlength:15; required), `Poliklinik ID` (string; maxlength: 10; required), `Date` (date; min:tomorrow; required), `Start Time` (time; required), `End Time` (time; required) [cite: 198] | [cite_start]**HTTP Status Code:** 200 [cite: 198][cite_start], **Body:** `"message": "Schedule modified"` [cite: 198] | [cite_start]**Body Status Code:** 422[cite: 201], **Body:** `"message": "Invalid field", "errors": {"doctorID": ["Doctor field is required." 205], "PoliklinikID": [1, "Poliklinik field is required." 1], "date": [ "Date field is required. | Minimal tomorrow" 1], "startTime": ["Start Time field is required." 1], "endTime": ["End Time field is required." [cite_start]1]}}` [cite: 202, 203, 204, 206, 207, 208, 209, 210, 211, 212, 213, 214, 215, 216, 217, 218] | [cite_start]**HTTP Status Code:** 404 [cite: 220][cite_start], **Body:** `"message": "Schedule not found"` [cite: 222] | [cite_start]**HTTP Status Code:** 401 [cite: 224][cite_start], **Body:** `1 "message": "Unauthenticated."` [cite: 225]

#### c. Delete Schedule

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/api/v3/schedule/:id` | `DELETE` | Admin can delete a schedule. The schedule cannot be deleted once the date has passed the current date. |

| Request | Response Success | Response Constraint Error | Response Not Found | Response Invalid Token |
| :--- | :--- | :--- | :--- | :--- |
| **Headers:** `Authorization: Bearer <token>` | **HTTP Status Code:** 204 | **HTTP Status Code:** 422, **Body:** `{ "message": "Schedule cannot deleted"` | **HTTP Status Code:** 404, **Body:** `{ "message": "Schedule not found"` | **HTTP Status Code:** 401, **Body:** `{ "message": "Unauthenticated."` |

#### d. Get All Schedules

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/api/v3/schedule` | `GET` | Admin to get all schedules data |

| Request | Response Success | Response Invalid Params | Response Invalid Token |
| :--- | :--- | :--- | :--- |
| **Headers:** `Authorization: Bearer <token>`, **Params:** `page` (integer, minimum 0 and default 0), `size` (integer, minimum 1 and default 10) | **HTTP Status Code:** 200, **Body:** `{ "page": 0, "size": 10, "schedule": [{"scheduleID": 1, "doctorID": "DOC000000000001", "doctorName": "Fulan", "poliklinikID": "DEPT000001", "PoliklinikName": "Poli Umum", "scheduleDate": "2025-01-30", "startTime": "09:00", "endTime": "15:00", "created at": "2025-01-20 00:34:10", "updatedAt": null}]}` | **HTTP Status Code:** 422, **Body:** `{"message": "Invalid field", "errors": {"page": ["The page field must be at least 0." 1], "size": ["The size field must be a number." 1]}}` | **HTTP Status Code:** 401, **Body:** `{ "message": "Unauthenticated."` |

---

## SERVER SIDE MODULE PART II (FRONTEND DEVELOPMENT)

### CONTENTS

This module has the following files:
1.  `MODULE_SERVER_SIDE_JT1_25.docx`
2.  `MODULE_SERVER_SIDE_JT1_25.pdf`
3.  `MODULE_SERVER_SIDE_MEDIA.zip`

Template HTML is provided. You are required to use the template and you are recommended to modify the template design without affecting the functionality of the frontend.

| Page | Description Tasks |
| :--- | :--- |
| **General** | - Document title should be reflected on the current page. |
| | - Display username and logout button on the navbar after login success. |
| | - Clicking username will go to the logged in user profile page. |
| | - Users can log out after clicking the logout button on the navbar. |
| **Login** | - If a user is logged in, the page will be redirected to its own user profile page. |
| | - Users can login with existing credentials. |
| | - If login fails, display all of the error messages. |
| | - If logged in user try to access this page, the page should be redirected. to own user profile page |
| **Poliklinik** | - On the "Poliklinik" menu, the admin can add a new Poliklinik. |
| | - Admin can update and delete existing data, but you cannot do that if there are schedules attached. |
| | - Poliklinik ID must be a string, no space and consists of 10 Alphanumeric. |
| | - Poliklinik Name must be a string. |
| | - Description must be a string and optional. |
| **Doctor** | - On "Doctor" menu, admin can add new doctor |
| | - Admin can update and delete existing data, but you cannot do that if there are schedules attached. |
| | - Doctor ID must be a string, no space and consists of 15 Alphanumerics. |
| | - Name must be a string. |
| | - Gender must be a Female or Male with value F or M inserted. |
| | - Phone must be a string and maxlength 20. |
| | - Address must be a string. |
| | - Email must be a string. |
| | - Bio must be a string and optional. |
| **Schedule** | - On "schedule" menu, admin can add new schedule |
| | - Admin can update and delete existing data, but the schedule cannot be changed once the date has passed the current date. |
| | - No doctor and Poliklinik schedule time **can't overlap** with other schedules. |
| | - The rule cannot be applied backwards. |
| | - Doctor ID must be a string, consists of 15 Alphanumeric and match with Doctor ID in table `r_doctor`. |
| | - Poliklinik ID must be a string, consists of 10 Alphanumeric and match with Poliklinik ID in table `r_Poliklinik`. |
| | - Date must be date and minimum date is **tomorrow**. |
| | - Start Time must be time and minimum time is **6am**. |
| | - End Time must be time and minimum time is **6am**. |

---

## ER DIAGRAM

### Database Schema

| Table Name | Column Name | Data Type | Constraint |
| :--- | :--- | :--- | :--- |
| `simra_users` | `user_id` | int(11) | PK |
| | `user_username` | varchar(255) | |
| | `user_password` | varchar(255) | |
| | `created_at` | datetime | |
| | `updated_at` | datetime | |
| `simra_poliklinik` | `pol_id` | varchar(10) | PK |
| | `pol_name` | varchar(255) | |
| | `pol_description` | text | |
| | `created_at` | timestamp | |
| | `updated_at` | datetime | |
| `simra_schedules` | `schedule_id` | int(11) | PK |
| | `doctor_id` | varchar(15) | FK |
| | `pol_id` | varchar(10) | FK |
| | `schedule_date` | date | |
| | `schedule_start_time` | time | |
| | `schedule_end_time` | time | |
| | `created_at` | timestamp | |
| | `updated_at` | datetime | |
| `simra_doctors` | `doctor_id` | varchar(15) | PK |
| | `doctor_name` | varchar(255) | |
| | `doctor_gender` | varchar(1) | |
| | `doctor_phone` | varchar(20) | |
| | `doctor_address` | varchar(255) | |
| | `doctor_email` | varchar(255) | |
| | `doctor_bio` | text | |
| | `created_at` | timestamp | |
| | `updated_at` | datetime | |

---

## MEDIA FILES

* Frameworks (laravel, react and vue)
* Template HTML (based on bootstrap v5.3)

## INSTRUCTION FOR COMPETITORS

1.  Database (`db-healthcare.sql`) and ER diagram (`db-diagram.pdf`) should be exported and saved under the desktop folder **`XX_SERVER_MODULE ( Backend / Frontend )`** where *xx* is PC number.
2.  REST Api should be reached on **`<host>/XX/backend`** where *xx* is PC number.
3.  Frontend app should be reached on **`<host>/XX/frontend`** where *xx* is PC number.
4.  Zip **`XX_SERVER_MODULE`** and saved under the desktop folder. Make sure to **exclude** `vendor` and `node_modules` folder when zipping files.
```
