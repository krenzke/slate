---
title: MGR API Documentation
language_tabs:
  - json: JSON
  - shell: cURL
---

## REST API for the MGR platform.

### Authentication

Authentication is done via an **Authorization** Header. Successfully signing in as
a user, business staff, app, etc. will return an api token. This token can be
sent with all subsequent requests via the **Authorization: Bearer {your-api-token}** header.

# Business Accounts

A Business Account is a gym or studio with one or many locations.
It is the top-level entity for pretty much everything.
By accessing the API from a specific domain, you are generally mapping to a specific business account.
Generally, this will be called once when the app loads. For example, if the user visits http://www.joes-gym.com
and the web app makes a fetch call to **/api/business_account/current**, the API will look at the
ORIGIN header, and return the data associated with the Joes Gym Business Account.


## Get Current

Ask the API for what my current Business Account is based on host origin.

### Request

#### Endpoint

```plaintext
GET /api/business_accounts/current
Origin: http://pollich.ca
Host: example.org
Cookie: 
```

`GET /api/business_accounts/current`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;1bc8684b45aed3a046fafb2c373de3b1&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3948c301-b5aa-4293-bb34-b9c8804d6923
X-Runtime: 0.009059
Content-Length: 1375
200 OK
```


```json
{
  "business_account": {
    "id": "578ca6ff-1a66-4645-acf4-ffdb54e17602",
    "name": "Hirthe-Daugherty",
    "slug": "hirthe-daugherty",
    "business_type": "fitness_studio",
    "account_type": null,
    "requires_waiver": true,
    "waiver_text": null,
    "waiver_url": null,
    "locations": [
      {
        "id": "9961e230-d2bd-4bca-b970-bdc52d72fd25",
        "name": "Walker-Steuber",
        "slug": "walker-steuber",
        "address1": null,
        "address2": null,
        "city": null,
        "state": null,
        "zip_code": null,
        "contact_email": null,
        "phone": null,
        "latitude": null,
        "longitude": null,
        "time_zone": "America/Los_Angeles",
        "allow_guest_only_reservations": true,
        "show_waitlist_capacity": true,
        "default_schedule_display_period": null
      },
      {
        "id": "bcb4965f-4656-4464-907a-1304c0393829",
        "name": "Prosacco-Kilback",
        "slug": "prosacco-kilback",
        "address1": null,
        "address2": null,
        "city": null,
        "state": null,
        "zip_code": null,
        "contact_email": null,
        "phone": null,
        "latitude": null,
        "longitude": null,
        "time_zone": "America/Los_Angeles",
        "allow_guest_only_reservations": true,
        "show_waitlist_capacity": true,
        "default_schedule_display_period": null
      }
    ],
    "roles": [
      {
        "id": "f228aa01-2529-4715-8be3-cc4178e87877",
        "name": "Super Admin",
        "slug": "super-admin",
        "permissions": [
          "marketing-reports",
          "refunds",
          "edit-user-profile",
          "business-reports",
          "price-adjustment",
          "schedule-adjustment"
        ]
      },
      {
        "id": "da93a4e4-eb49-4a14-8c10-d7ffa336a6f6",
        "name": "Instructor",
        "slug": "instructor",
        "permissions": [
          "refunds",
          "edit-user-profile",
          "schedule-adjustment"
        ]
      }
    ]
  }
}
```



# Business Staff

Anyone who works for a Business Account. Most commonly, you'll want to get a list of instructors teaching classes.

## Filter By Role


### Request

#### Endpoint

```plaintext
GET /api/business_staffs?roles[]=instructor
Origin: http://schaefer-medhurst.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/business_staffs`

#### Parameters


```json
roles: [&quot;instructor&quot;]
```


| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| q  | Search by Name |
| roles  | List of roles to filter by |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;fe5c0d8a26f91685386772a12be45f65&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2089fe29-b4ff-4343-9411-c3a5ab4e06bd
X-Runtime: 0.045134
Content-Length: 1093
200 OK
```


```json
{
  "business_staffs": [
    {
      "id": "5cad7782-55da-4559-bf2f-83cc48d68dce",
      "email": "betsey@toygraham.biz",
      "slug": "elly-cassin",
      "first_name": "Elly",
      "last_name": "Cassin",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": null,
      "roles": [
        {
          "id": "1e3b5eb3-8c66-439e-bd19-6600a71d7238",
          "name": "Instructor",
          "slug": "instructor",
          "permissions": [
            "refunds",
            "edit-user-profile",
            "schedule-adjustment"
          ]
        }
      ],
      "permissions": [
        "refunds",
        "edit-user-profile",
        "schedule-adjustment"
      ],
      "pay_rates": [

      ],
      "social_connections": [

      ]
    },
    {
      "id": "a0798e3b-6119-41b4-83a0-fea0a98f8899",
      "email": "terrilyn@maggio.com",
      "slug": "elenor-stracke",
      "first_name": "Elenor",
      "last_name": "Stracke",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": null,
      "roles": [
        {
          "id": "1e3b5eb3-8c66-439e-bd19-6600a71d7238",
          "name": "Instructor",
          "slug": "instructor",
          "permissions": [
            "refunds",
            "edit-user-profile",
            "schedule-adjustment"
          ]
        }
      ],
      "permissions": [
        "refunds",
        "edit-user-profile",
        "schedule-adjustment"
      ],
      "pay_rates": [

      ],
      "social_connections": [

      ]
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 2,
    "per_page": 100
  }
}
```



## Get All


### Request

#### Endpoint

```plaintext
GET /api/business_staffs
Origin: http://lemke-inc.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/business_staffs`

#### Parameters



| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| q  | Search by Name |
| roles  | List of roles to filter by |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;bd7141e975676f8aca261e513b3d017b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d4aec4c7-5a6d-407f-810b-1adb5b656c6a
X-Runtime: 0.077752
Content-Length: 1669
200 OK
```


```json
{
  "business_staffs": [
    {
      "id": "30a46905-c16b-47b5-9b4b-6f3da85615a0",
      "email": "tomoko.reichert@hilll.co.uk",
      "slug": "lorina-legros",
      "first_name": "Lorina",
      "last_name": "Legros",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": null,
      "roles": [

      ],
      "permissions": [

      ],
      "pay_rates": [

      ],
      "social_connections": [

      ]
    },
    {
      "id": "1a8d766a-3bae-4fa8-9481-37bb82820775",
      "email": "jammie@simonis.biz",
      "slug": "etha-mertz",
      "first_name": "Etha",
      "last_name": "Mertz",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": null,
      "roles": [

      ],
      "permissions": [

      ],
      "pay_rates": [

      ],
      "social_connections": [

      ]
    },
    {
      "id": "d54a4547-d299-427b-b8e6-001e5ca6a4fb",
      "email": "kami@wisozkoberbrunner.us",
      "slug": "deneen-sanford",
      "first_name": "Deneen",
      "last_name": "Sanford",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": null,
      "roles": [
        {
          "id": "31652f96-0f71-48fd-8d32-cadab68150da",
          "name": "Instructor",
          "slug": "instructor",
          "permissions": [
            "refunds",
            "edit-user-profile",
            "schedule-adjustment"
          ]
        }
      ],
      "permissions": [
        "refunds",
        "edit-user-profile",
        "schedule-adjustment"
      ],
      "pay_rates": [

      ],
      "social_connections": [

      ]
    },
    {
      "id": "561be62b-3e30-482d-8ac9-74cd9eb36b20",
      "email": "edwina_welch@daniel.co.uk",
      "slug": "gerda-prosacco",
      "first_name": "Gerda",
      "last_name": "Prosacco",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": null,
      "roles": [
        {
          "id": "31652f96-0f71-48fd-8d32-cadab68150da",
          "name": "Instructor",
          "slug": "instructor",
          "permissions": [
            "refunds",
            "edit-user-profile",
            "schedule-adjustment"
          ]
        }
      ],
      "permissions": [
        "refunds",
        "edit-user-profile",
        "schedule-adjustment"
      ],
      "pay_rates": [

      ],
      "social_connections": [

      ]
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 4,
    "per_page": 100
  }
}
```



# Gift Cards

Can be redeemed for cash (account balance) or packages

## Redeem Cash Gift Card


### Request

#### Endpoint

```plaintext
POST /api/gift_cards/redeem
Origin: http://raynor-pollich.mgrapp.com
Authorization: Bearer 88e29bfd-2e61-4e51-95ad-92dc34582273
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/gift_cards/redeem`

#### Parameters


```json
code=C50CF1DC
```


| Name | Description |
|:-----|:------------|
| code *required* | Gift Card Code |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;97e4534082d6c4d37fe12734d56ac180&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 94d51d73-f5ae-4b39-a801-97cd05c5a29b
X-Runtime: 0.064949
Content-Length: 1162
201 Created
```


```json
{
  "gift_card_instance": {
    "id": "0faf9cd8-20b0-4dd6-a439-de4d7fc8fe28",
    "gift_card_type": "cash",
    "amount": "14.0",
    "code": "C50CF1DC",
    "num_sessions": 0,
    "created_at": "2018-12-30T17:52:18.010Z",
    "redeemed_at": "2018-12-30T17:52:18.031Z",
    "redeemer": {
      "email": "callie@fay.ca"
    }
  },
  "transaction": {
    "id": "1d3111a3-0577-4c6b-a69e-54bcda616abc",
    "created_at": "2018-12-30T17:52:18.061Z",
    "state": "complete",
    "amount": "-14.0",
    "fail_message": null,
    "process_after": null,
    "processed_at": "2018-12-30T17:52:18.070Z",
    "payment_type": "account_balance",
    "description": null,
    "payment_source_invalid": false,
    "payment_method": {
      "id": 0,
      "source_id": null,
      "payment_type": "account_balance",
      "brand": null,
      "exp_month": null,
      "exp_year": null,
      "last4": null,
      "balance": "114.0",
      "is_default": null
    },
    "transactable": null,
    "creator_type": null,
    "creator": null
  },
  "package_instance": null,
  "user_profile": {
    "id": "5a112173-6a1d-4399-a7ee-e2708745339d",
    "account_balance": "114.0",
    "signed_waiver_at": null,
    "created_at": "2018-12-30T17:52:18.020Z",
    "email": "callie@fay.ca",
    "first_name": "Marlen",
    "last_name": "Quigley",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2018-12-30"
  }
}
```



# Offerings

Specific instances of a class that a user can sign up for

## Filter By Location


### Request

#### Endpoint

```plaintext
GET /api/offerings?time_zone_offset=420&amp;location_id=a3c98b38-0d6c-472d-887d-d525801eadb1
Origin: http://abernathy-llc.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/offerings`

#### Parameters


```json
time_zone_offset: 420
location_id: a3c98b38-0d6c-472d-887d-d525801eadb1
```


| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| time_zone_offset  | Time Zone Offset, since time zones might matter |
| start_date  | Filter by date (inclusive) |
| end_date  | Filter by date (inclusive) |
| resource_id  | Filter by resource |
| business_staff_id  | Filter by instructor (or sub) |
| location_id  | Filter by location |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;fefab9b76b7922c755b95a8464e4b271&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5b19ff72-c9e3-4813-86a0-6fca3cf61fc4
X-Runtime: 0.012589
Content-Length: 4674
200 OK
```


```json
{
  "offerings": [
    {
      "id": "0ed1d2bb-a20e-4686-8522-b44a65060313",
      "name": "Melting Sheep fa140bb7",
      "resource_slug": "melting-sheep-fa140bb7",
      "description": "When the rennet is added, curds are formed taste and texture in all colours but poets have been mysteriously silent on the subject of cheese - tongue in cheek garlic cheese biscuits the milky way of blessed are the cheesemakers raw milk is unpasteurized - tongue in cheek they can also age quite well in ripening cellars where.",
      "resource_type": null,
      "start_time": "2018-08-21T09:00:00.000Z",
      "end_time": "2018-08-21T10:00:00.000Z",
      "reservation_cutoff_time": "2018-08-21T09:00:00.000Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-08-21T09:00:00.000Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-08-21T09:00:00.000Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Labadie, O'Reilly and DuBuque",
      "location_id": "a3c98b38-0d6c-472d-887d-d525801eadb1",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "a621df30-a908-46bc-8dc6-c599dd3ed750",
        "email": "jeanmarie.mann@wintheiserdach.name",
        "slug": "hal-reilly",
        "first_name": "Hal",
        "last_name": "Reilly",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "e1988669-cf6a-42ce-a681-5ca126024e1f",
      "name": "Fat Goats 5dafb89c",
      "resource_slug": "fat-goats-5dafb89c",
      "description": "Separate the curds from the wey processed cheese has several technical advantages over traditional cheese of the Friesian herd - tongue in cheek team cheesy says hi when the rennet is added, curds are formed of the Friesian herd garlic cheese biscuits when the rennet is added, curds are formed separate the curds from the wey.",
      "resource_type": null,
      "start_time": "2018-08-22T05:00:00.000Z",
      "end_time": "2018-08-22T06:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T05:00:00.000Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-08-22T05:00:00.000Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-08-22T05:00:00.000Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Labadie, O'Reilly and DuBuque",
      "location_id": "a3c98b38-0d6c-472d-887d-d525801eadb1",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "7e68c6f9-8686-4988-a3e8-e85c4107001b",
        "email": "kassie_dicki@binsturner.us",
        "slug": "bernard-batz",
        "first_name": "Bernard",
        "last_name": "Batz",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "7ac0cd4d-d0ad-43d5-900a-498584457530",
      "name": "Melting Sheep fa140bb7",
      "resource_slug": "melting-sheep-fa140bb7",
      "description": "When the rennet is added, curds are formed taste and texture in all colours but poets have been mysteriously silent on the subject of cheese - tongue in cheek garlic cheese biscuits the milky way of blessed are the cheesemakers raw milk is unpasteurized - tongue in cheek they can also age quite well in ripening cellars where.",
      "resource_type": null,
      "start_time": "2018-08-22T17:00:00.000Z",
      "end_time": "2018-08-22T18:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T17:00:00.000Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-08-22T17:00:00.000Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-08-22T17:00:00.000Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Labadie, O'Reilly and DuBuque",
      "location_id": "a3c98b38-0d6c-472d-887d-d525801eadb1",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "1ff72ad6-8984-477d-b082-5dda830ee7ad",
        "email": "latisha_block@stark.biz",
        "slug": "sonny-gerhold",
        "first_name": "Sonny",
        "last_name": "Gerhold",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    }
  ],
  "reservations": [

  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 3,
    "per_page": 100
  }
}
```



## Get All


### Request

#### Endpoint

```plaintext
GET /api/offerings?time_zone_offset=420
Origin: http://gulgowski-kiehn.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/offerings`

#### Parameters


```json
time_zone_offset: 420
```


| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| time_zone_offset  | Time Zone Offset, since time zones might matter |
| start_date  | Filter by date (inclusive) |
| end_date  | Filter by date (inclusive) |
| resource_id  | Filter by resource |
| business_staff_id  | Filter by instructor (or sub) |
| location_id  | Filter by location |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;86560fc81400cca20a6af8bdbfe6d496&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f6d85042-418c-4552-96de-77ae1de45426
X-Runtime: 0.022787
Content-Length: 4898
200 OK
```


```json
{
  "offerings": [
    {
      "id": "dfb728e8-9630-48d3-8db7-c7676ebc9957",
      "name": "Cheeky Affineurs fea2b24e",
      "resource_slug": "cheeky-affineurs-fea2b24e",
      "description": "Double dutch or so cute but cheesy but round cheeses are to be cut in wedges, like a cake but poets have been mysteriously silent on the subject of cheese What do you call cheese that isn't yours? Nacho Cheese; the sticky nature of processed cheese can make it difficult to slice, but in an artisan farmerhouse blue fungi in cream say cheese processed cheese has several technical advantages over traditional cheese.",
      "resource_type": null,
      "start_time": "2018-08-21T09:00:00.000Z",
      "end_time": "2018-08-21T10:00:00.000Z",
      "reservation_cutoff_time": "2018-08-21T09:00:00.000Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-08-21T09:00:00.000Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-08-21T09:00:00.000Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Gusikowski and Sons",
      "location_id": "901effe7-4182-49ed-850d-e7ea1dbaeef3",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "08949a15-03fd-4b64-b614-17d07828e8ca",
        "email": "natisha_roberts@kuvalis.biz",
        "slug": "marnie-bernhard",
        "first_name": "Marnie",
        "last_name": "Bernhard",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "8b1ae29b-4189-4741-8a8a-9c2090ad7e6b",
      "name": "Milky Affineurs 9791d0b1",
      "resource_slug": "milky-affineurs-9791d0b1",
      "description": "Applewood smoked of cheesy business lingo bergkäse from the Alps he old cheese dairy buildings, situated on the historic site he old cheese dairy buildings, situated on the historic site but poets have been mysteriously silent on the subject of cheese trying too hard, unsubtle, and inauthentic Sheridans Cheesemongers dutch sandwich but round cheeses are to be cut in wedges, like a cake.",
      "resource_type": null,
      "start_time": "2018-08-22T05:00:00.000Z",
      "end_time": "2018-08-22T06:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T05:00:00.000Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-08-22T05:00:00.000Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-08-22T05:00:00.000Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Gusikowski and Sons",
      "location_id": "901effe7-4182-49ed-850d-e7ea1dbaeef3",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "5ad4f45c-fb2c-418c-9089-e9d38f7eebc4",
        "email": "petrina@koch.com",
        "slug": "tonja-will",
        "first_name": "Tonja",
        "last_name": "Will",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "f1d5e845-3b0c-4d3f-beac-2516e6817c17",
      "name": "Cheeky Affineurs fea2b24e",
      "resource_slug": "cheeky-affineurs-fea2b24e",
      "description": "Double dutch or so cute but cheesy but round cheeses are to be cut in wedges, like a cake but poets have been mysteriously silent on the subject of cheese What do you call cheese that isn't yours? Nacho Cheese; the sticky nature of processed cheese can make it difficult to slice, but in an artisan farmerhouse blue fungi in cream say cheese processed cheese has several technical advantages over traditional cheese.",
      "resource_type": null,
      "start_time": "2018-08-22T17:00:00.000Z",
      "end_time": "2018-08-22T18:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T17:00:00.000Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-08-22T17:00:00.000Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-08-22T17:00:00.000Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Gusikowski and Sons",
      "location_id": "901effe7-4182-49ed-850d-e7ea1dbaeef3",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "e1d30b47-4893-415e-95a4-f00db29f05c8",
        "email": "laticia@lebsack.com",
        "slug": "margie-mitchell",
        "first_name": "Margie",
        "last_name": "Mitchell",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    }
  ],
  "reservations": [

  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 3,
    "per_page": 100
  }
}
```



# Orders

Purchasing one or more items

## Buying a Package


### Request

#### Endpoint

```plaintext
POST /api/orders
Origin: http://bernier-boyer.mgrapp.com
Authorization: Bearer 61d1635d-6600-40c2-897d-413e6d7ca6f6
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders`

#### Parameters


```json
line_items[][variant_id]=4e348be6-9fc5-41c0-bd4e-058a8bde9474&line_items[][quantity]=1&payments[][payment_type]=stripe_cc&payments[][source_id]=test_cc_2
```


| Name | Description |
|:-----|:------------|
| line_items *required* | List of items ({variant_id:, quantity:}) |
| payments *required* | List of payments ({payment_type:, source_id:}) |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;e1f96db30d105f378bd96cb300794c77&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1700cd3d-994d-4429-8272-0ab83d5ce3a7
X-Runtime: 0.104268
Content-Length: 1563
201 Created
```


```json
{
  "order": {
    "id": "522f6a1d-f0f0-4d76-b87a-de395ee8d4ad",
    "number": "522f6a1d",
    "line_items": [
      {
        "id": "5812148a-e337-493e-bde3-aba739d86a2c",
        "quantity": 1,
        "per_unit_price": "70.0",
        "name": "VU Power Gel Receiver",
        "variant": {
          "id": "4e348be6-9fc5-41c0-bd4e-058a8bde9474",
          "price": "70.0",
          "is_master": true
        }
      }
    ],
    "created_at": "2018-12-30T17:52:18.913Z",
    "total": "0.0",
    "item_total": "70.0",
    "adjustment_total": "0.0",
    "payment_total": "70.0",
    "payment_state": "complete",
    "fulfillment_state": "complete",
    "user": {
      "id": "d4d2c279-3d2b-4a5d-b706-0f875d3f3698",
      "account_balance": "0.0",
      "signed_waiver_at": null,
      "created_at": "2018-12-30T17:52:18.843Z",
      "email": "keira_moen@yost.biz",
      "first_name": "Shanita",
      "last_name": "Brakus",
      "address1": null,
      "address2": null,
      "city": null,
      "state": null,
      "zip_code": null,
      "phone": null,
      "dob": null,
      "member_start_date": "2018-12-30"
    },
    "payments": [
      {
        "id": "5abf4dc5-7f45-48d8-8a99-13bcc3ddedb3",
        "created_at": "2018-12-30T17:52:18.919Z",
        "state": "complete",
        "amount": "70.0",
        "fail_message": null,
        "process_after": null,
        "processed_at": "2018-12-30T17:52:18.940Z",
        "payment_type": "stripe_cc",
        "description": null,
        "payment_source_invalid": false,
        "payment_method": {
          "id": "test_cc_2",
          "source_id": "test_cc_2",
          "payment_type": "stripe_cc",
          "brand": "Visa",
          "exp_month": 11,
          "exp_year": 2099,
          "last4": "1234",
          "balance": null,
          "is_default": true
        },
        "transactable": {
          "type": "order",
          "id": "522f6a1d-f0f0-4d76-b87a-de395ee8d4ad",
          "number": "522f6a1d",
          "total": "0.0",
          "item_total": "70.0",
          "adjustment_total": "0.0",
          "payment_total": "70.0",
          "payment_state": "complete",
          "fulfillment_state": "complete"
        },
        "creator_type": null,
        "creator": null
      }
    ]
  }
}
```



# Payment Methods

Ways in which a user can pay for services. Currently just Stripe credit cards and account balance.

## Create New


### Request

#### Endpoint

```plaintext
POST /api/payment_methods
Origin: http://oberbrunner-and-sons.mgrapp.com
Authorization: Bearer 9ba1a1e4-36f8-430f-a9b2-1ade3ed6c86b
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/payment_methods`

#### Parameters


```json
stripe_token=test_tok_1
```


| Name | Description |
|:-----|:------------|
| stripe_token *required* | Token returned by Stripe SDK |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;02eda27274dacb5d255f29524466cc3f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2fb20350-f3bc-429b-bfd0-d4b544a6655e
X-Runtime: 0.010772
Content-Length: 181
201 Created
```


```json
{
  "payment_method": {
    "id": "test_cc_2",
    "source_id": "test_cc_2",
    "payment_type": "stripe_cc",
    "brand": "Visa",
    "exp_month": 9,
    "exp_year": 2018,
    "last4": "4242",
    "balance": null,
    "is_default": null
  }
}
```



## Get Available


### Request

#### Endpoint

```plaintext
GET /api/payment_methods
Origin: http://west-gottlieb-and-hammes.mgrapp.com
Authorization: Bearer e5506e6b-f855-4126-ad6f-a267d6d200f7
Host: example.org
Cookie: 
```

`GET /api/payment_methods`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;7216d8771b3dc03ea716050a31fed360&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0527acc7-21e7-4d77-889e-96463881223c
X-Runtime: 0.013311
Content-Length: 339
200 OK
```


```json
{
  "payment_methods": [
    {
      "id": "test_cc_2",
      "source_id": "test_cc_2",
      "payment_type": "stripe_cc",
      "brand": "Visa",
      "exp_month": 11,
      "exp_year": 2099,
      "last4": "1234",
      "balance": null,
      "is_default": true
    },
    {
      "id": 0,
      "source_id": null,
      "payment_type": "account_balance",
      "brand": null,
      "exp_month": null,
      "exp_year": null,
      "last4": null,
      "balance": "100.0",
      "is_default": null
    }
  ]
}
```



# Products

Anything that can be purchased by a user. Includes packages, gift cards, and physical items.

## Filter By Type


### Request

#### Endpoint

```plaintext
GET /api/products?type=package
Origin: http://bahringer-schmeler-and-bernier.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
type: package
```


| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| q  | Search by Name |
| type  | Filter by Product Type |
| resource_offering_id  | Filter packages by applicability to given offering |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;5a5c6629e057dbd564186f7c9b6b1cc6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4993c204-8b68-4543-8f69-246fac1dfdcd
X-Runtime: 0.011717
Content-Length: 1667
200 OK
```


```json
{
  "products": [
    {
      "id": "c3eff894-f50a-47ce-98fc-980c59449158",
      "name": "Lucell Gel Bridge",
      "slug": "lucell-gel-bridge",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "a608f699-1a89-4a4b-bdde-753c4c5441f0",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "first_instance_is_free": true,
        "waitlist_priority": 1
      },
      "gift_card": null,
      "variants": [
        {
          "id": "9e7935f8-0ae7-47eb-a770-566177cf0efb",
          "price": "74.0",
          "is_master": true
        }
      ],
      "price": "74.0",
      "image": null
    },
    {
      "id": "17a0217d-b745-45ca-9ac3-889e6fa4c510",
      "name": "Aftercell Gel Video Bridge",
      "slug": "aftercell-gel-video-bridge",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "43e21d5c-b5ed-4be2-827b-dfc75c55678e",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "first_instance_is_free": true,
        "waitlist_priority": 1
      },
      "gift_card": null,
      "variants": [
        {
          "id": "15ce0f7f-25f6-480f-86be-f99f4098735d",
          "price": "36.0",
          "is_master": true
        }
      ],
      "price": "36.0",
      "image": null
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 2,
    "per_page": 100
  }
}
```



## Get All


### Request

#### Endpoint

```plaintext
GET /api/products
Origin: http://mcdermott-inc.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters



| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| q  | Search by Name |
| type  | Filter by Product Type |
| resource_offering_id  | Filter packages by applicability to given offering |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;50a8f0b89e64b0a32a8637aeb8a62b1c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cd01ed5a-566b-4df4-a9fd-edba93ac5c23
X-Runtime: 0.017002
Content-Length: 2833
200 OK
```


```json
{
  "products": [
    {
      "id": "a82b651b-4530-489d-a72c-08101dc19059",
      "name": "Pyneforge Video Mount",
      "slug": "pyneforge-video-mount",
      "description": null,
      "product_type": "normal",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": null,
      "variants": [
        {
          "id": "2be2a94f-7779-40f2-a9c2-7648de62a408",
          "price": "57.0",
          "is_master": true
        }
      ],
      "price": "57.0",
      "image": null
    },
    {
      "id": "7bec7d3c-a2f7-412a-8dd4-a496937615d7",
      "name": "Lucell Audible Amplifier",
      "slug": "lucell-audible-amplifier",
      "description": null,
      "product_type": "normal",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": null,
      "variants": [
        {
          "id": "e77056a1-f2e4-4ecc-9875-871c079cdba0",
          "price": "49.0",
          "is_master": true
        }
      ],
      "price": "49.0",
      "image": null
    },
    {
      "id": "aa09a7a1-3c2d-47c2-beba-bcbeabd1b56b",
      "name": "Reusche Side System",
      "slug": "reusche-side-system",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "b6a32d7e-ecb4-4c24-91fe-55b9e59a5324",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "first_instance_is_free": true,
        "waitlist_priority": 1
      },
      "gift_card": null,
      "variants": [
        {
          "id": "a1583ae9-11a6-4d5b-9adf-1aa84f26ccb2",
          "price": "73.0",
          "is_master": true
        }
      ],
      "price": "73.0",
      "image": null
    },
    {
      "id": "bdcb482d-8057-4d04-9671-d84e7d82e35c",
      "name": "Trintwood Video Component",
      "slug": "trintwood-video-component",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "fceaa0b1-8039-4bb4-9798-db2faadb8c52",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "first_instance_is_free": true,
        "waitlist_priority": 1
      },
      "gift_card": null,
      "variants": [
        {
          "id": "edb3ad5d-a297-45d6-9897-84876c3e1826",
          "price": "22.0",
          "is_master": true
        }
      ],
      "price": "22.0",
      "image": null
    },
    {
      "id": "830a91c4-073f-406d-a0c6-1af40107f9a5",
      "name": "Cygfunc Remote HD Bracket",
      "slug": "cygfunc-remote-hd-bracket",
      "description": null,
      "product_type": "gift_card",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": {
        "id": "08d4f464-ecad-4cf0-a413-b654431c58ac",
        "gift_card_type": "cash",
        "fixed_amount": true,
        "amount": "20.0",
        "num_sessions": 0
      },
      "variants": [
        {
          "id": "3f31be69-853d-42ab-b26d-6eaa61b8fce6",
          "price": "33.0",
          "is_master": true
        }
      ],
      "price": "33.0",
      "image": null
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 5,
    "per_page": 100
  }
}
```



# Reservations

Specific instance of a user signing up for an offering

## Create New


### Request

#### Endpoint

```plaintext
POST /api/reservations
Origin: http://sipes-llc.mgrapp.com
Authorization: Bearer 09537af6-a62a-405b-a806-afa4d91ded60
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/reservations`

#### Parameters


```json
resource_offering_id=a5b5cf3b-7bb3-4b6e-8f0e-64d53d9168ea&package_instance_id=64306062-6927-43cc-944e-029a1c292aa8
```


| Name | Description |
|:-----|:------------|
| stripe_token *required* | Token returned by Stripe SDK |
| resource_offering_id *required* | Id of offering to sign up for |
| package_instance_id *required* | Id of package used to pay for reservation |
| is_guest  | Reservation is for a guest? |
| guest_name  | Guest Name |
| guest_email  | Guest Email |
| guest_phone  | Guest Phone |
| accepts_waiver  | If user accepts waiver |
| note  | Note to the instructor |
| recurrence[start_date]  | Recurrence Start Date |
| recurrence[end_date]  | Recurrence End Date |
| recurrence[on_monday]  | Include Monday recurrences |
| recurrence[on_tuesday]  | Include Tuesday recurrences |
| recurrence[on_wednesday]  | Include Wednesday recurrences |
| recurrence[on_thursday]  | Include Thursday recurrences |
| recurrence[on_friday]  | Include Friday recurrences |
| recurrence[on_saturday]  | Include Saturday recurrences |
| recurrence[on_sunday]  | Include Sunday recurrences |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;995dea1750bb6caea0a9128834ebf638&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 46cd2fe0-3594-4bbe-9b83-40c890e841ff
X-Runtime: 0.061330
Content-Length: 3311
201 Created
```


```json
{
  "reservations": [
    {
      "id": "5c4bb9e1-a3cd-4aac-9849-114e061f770b",
      "state": "reserved",
      "created_at": "2018-12-30T17:52:18.489Z",
      "offering_id": "a5b5cf3b-7bb3-4b6e-8f0e-64d53d9168ea",
      "package_instance_id": "64306062-6927-43cc-944e-029a1c292aa8",
      "user": {
        "id": "c651702e-a0cc-425d-98b2-588388c1701a",
        "first_name": "Boris",
        "last_name": "Powlowski",
        "email": "carey@padberg.us"
      },
      "is_guest": false,
      "guest_email": null,
      "guest_name": null,
      "guest_phone": null,
      "note": null,
      "time_zone": "America/Los_Angeles",
      "start_time": "2018-12-30T18:52:18.439Z",
      "signed_in_at": null,
      "resource_name": "Nutty Dairy bd75d2d9",
      "package_name": "Brestforge Air Amplifier",
      "location_name": "Gislason, Dooley and Hilll",
      "package_expiration_date": null,
      "late_cancel_cutoff_time": "2018-12-30T18:52:18.439Z",
      "waitlist_cutoff_time": "2018-12-30T18:52:18.439Z",
      "end_time": "2018-12-30T19:52:18.439Z",
      "provider": {
        "first_name": "Daniela",
        "last_name": "O'Connell",
        "description": null,
        "slug": "daniela-o-connell"
      },
      "substitute": null
    }
  ],
  "offerings": [
    {
      "id": "a5b5cf3b-7bb3-4b6e-8f0e-64d53d9168ea",
      "name": "Nutty Dairy bd75d2d9",
      "resource_slug": "nutty-dairy-bd75d2d9",
      "description": "They were so cheesed off it is blue sky thinking the sticky nature of processed cheese can make it difficult to slice, but soft ripening cheese for but round cheeses are to be cut in wedges, like a cake of cheesy business lingo taste and texture in all colours when the rennet is added, curds are formed taste and texture in all colours the milky way of.",
      "resource_type": null,
      "start_time": "2018-12-30T18:52:18.439Z",
      "end_time": "2018-12-30T19:52:18.439Z",
      "reservation_cutoff_time": "2018-12-30T18:52:18.439Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2018-12-30T18:52:18.439Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2018-12-30T18:52:18.439Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 10,
      "num_total_reservations": 1,
      "time_zone": "America/Los_Angeles",
      "location_name": "Gislason, Dooley and Hilll",
      "location_id": "d9bde993-2e2a-4b13-b128-a9d33de2b883",
      "open_for_registration": true,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "5be6bad8-434f-4657-be5a-04f0b1113bfd",
        "email": "ada.kling@feestkeeling.us",
        "slug": "daniela-o-connell",
        "first_name": "Daniela",
        "last_name": "O'Connell",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": null
      },
      "substitute": null,
      "recurrence": null
    }
  ],
  "packages": [
    {
      "id": "64306062-6927-43cc-944e-029a1c292aa8",
      "name": "Brestforge Air Amplifier",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 10,
      "sessions_remaining": 10,
      "created_at": "2018-12-30T17:52:18.400Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "c651702e-a0cc-425d-98b2-588388c1701a",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-30T17:52:18.410Z",
          "email": "carey@padberg.us",
          "first_name": "Boris",
          "last_name": "Powlowski",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-30"
        }
      ]
    }
  ],
  "missing": null
}
```



# Resource

A.K.A. Classes. A Resource is the generic type of a
thing (e.g. Pilates, Vinyasa Yoga). Whereas an Offering is the specific instance of
it (e.g. Pilates at 8am on July 14 with Sarah)


## Get All


### Request

#### Endpoint

```plaintext
GET /api/resources
Origin: http://watsica-kulas-and-fahey.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/resources`

#### Parameters



| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| q  | Search by Name |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;036cc5e03380d4e94eaddb96c27f6715&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 910dba4c-5aea-4a40-910b-cb67879eb7e5
X-Runtime: 0.011433
Content-Length: 1627
200 OK
```


```json
{
  "resources": [
    {
      "id": "f17ac53e-a195-4f26-bbca-9d998f9d39c2",
      "name": "Cheeky Goats 205e5a15",
      "slug": "cheeky-goats-205e5a15",
      "description": "Separate the curds from the wey a good alternative to cheesecloth the early bird may get the worm, but the second mouse gets the cheese in the trap cheeseparing taste and texture in all colours taste and texture in all colours New York cheesecake blue fungi in cream when the rennet is added, curds are formed the slice of cheese is placed on top of the meat patty.",
      "resource_type": null,
      "image": null
    },
    {
      "id": "6c0231f9-9198-49ec-8aa0-cd793a38c4de",
      "name": "Grated Alpine fb715ffe",
      "slug": "grated-alpine-fb715ffe",
      "description": "Separate the curds from the wey in an artisan farmerhouse cheese paring with wine bergkäse from the Alps - tongue in cheek blessed are the cheesemakers trying too hard, unsubtle, and inauthentic the whiter and fresher the cheese, the crisper and fruitier the wine should be bergkäse from the Alps the sticky nature of processed cheese can make it difficult to slice, but.",
      "resource_type": null,
      "image": null
    },
    {
      "id": "7e229e78-7d2a-464d-812c-89edeb9f9613",
      "name": "Dutch Goats 96d75408",
      "slug": "dutch-goats-96d75408",
      "description": "But poets have been mysteriously silent on the subject of cheese so cute but cheesy is like chalk and cheese bergkäse from the Alps 10 grilled cheese sandwiches you should try immediately with cut to size washed curd cheese of the Friesian herd - tongue in cheek raw milk is unpasteurized.",
      "resource_type": null,
      "image": null
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 3,
    "per_page": 100
  }
}
```



# User Account

User profile and account information

## Get Session


### Request

#### Endpoint

```plaintext
GET /api/users/me
Origin: http://hermann-lebsack.mgrapp.com
Authorization: Bearer d28f8849-b3c2-4b41-b684-8073ba1b9b10
Host: example.org
Cookie: 
```

`GET /api/users/me`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;7eb3e408157e9476fec50b13db5709bd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f133b7b5-4690-4836-9ab5-a85d3dc09bc7
X-Runtime: 0.009334
Content-Length: 440
200 OK
```


```json
{
  "session": {
    "id": "d28f8849-b3c2-4b41-b684-8073ba1b9b10",
    "expires_at": "2019-01-13T17:52:17.784Z"
  },
  "user": {
    "id": "1537c475-2c57-4bbb-b971-200cc4d343ed",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2018-12-30T17:52:17.779Z",
    "email": "deeanna@zboncak.name",
    "first_name": "Kacie",
    "last_name": "Price",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2018-12-30"
  }
}
```



## Register


### Request

#### Endpoint

```plaintext
POST /api/users
Origin: http://jones-maggio.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users`

#### Parameters


```json
email=foo%40bar.com&password=password&first_name=Foo&last_name=Bar&address1=123+Fake+St.&address2=&city=Dallas&state=TX&zip_code=54682&phone=7896365485&dob=1980-01-01&accepts_waiver=1
```


| Name | Description |
|:-----|:------------|
| email *required* | Email |
| password *required* | Password |
| first_name *required* | First Name |
| last_name *required* | Last Name |
| address1  | Address |
| address2  | Address |
| city  | City |
| state  | State |
| zip_code  | Zip Code |
| phone  | Phone |
| dob  | Date of Birth |
| accepts_waiver  | Accepts waiver |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;e743200208bd9689e603eefcb451ec68&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6bf5b729-927a-4a07-a7aa-b19c96f894cf
X-Runtime: 0.015769
Content-Length: 458
201 Created
```


```json
{
  "session": {
    "id": "b1624f74-c145-4806-be8e-61c76c36f111",
    "expires_at": null
  },
  "user": {
    "id": "73c3b9c9-4f78-4d66-ba98-57f81161869d",
    "account_balance": "0.0",
    "signed_waiver_at": "2018-12-30T17:52:17.827Z",
    "created_at": "2018-12-30T17:52:17.828Z",
    "email": "foo@bar.com",
    "first_name": "Foo",
    "last_name": "Bar",
    "address1": "123 Fake St.",
    "address2": "",
    "city": "Dallas",
    "state": "TX",
    "zip_code": "54682",
    "phone": "7896365485",
    "dob": "1980-01-01",
    "member_start_date": "2018-12-30"
  }
}
```



## Sign In


### Request

#### Endpoint

```plaintext
POST /api/users/session
Origin: http://dicki-llc.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/session`

#### Parameters


```json
email=layla%40leannon.co.uk&password=password
```


| Name | Description |
|:-----|:------------|
| email *required* | Email |
| password *required* | Password |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;d41e029fc89c900c3187baa7c30b4621&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5640653c-4963-4ef2-86d0-5f4ccaae9ec0
X-Runtime: 0.009529
Content-Length: 420
201 Created
```


```json
{
  "session": {
    "id": "6d962514-654d-44ad-9b6f-468fcccf4ebb",
    "expires_at": null
  },
  "user": {
    "id": "3e2738c6-8a7e-4ce6-a785-58104aad0fea",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2018-12-30T17:52:17.844Z",
    "email": "layla@leannon.co.uk",
    "first_name": "Viki",
    "last_name": "Rosenbaum",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2018-12-30"
  }
}
```



## Sign Out


### Request

#### Endpoint

```plaintext
DELETE /api/users/session
Origin: http://block-inc.mgrapp.com
Authorization: Bearer ac905a19-1d12-4213-a501-9d3617371a9f
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`DELETE /api/users/session`

#### Parameters


None known.


### Response

```plaintext
Status: 200
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
Cache-Control: no-cache
X-Request-Id: fabd1440-b66f-4c0d-b0c0-72f8461ccda8
X-Runtime: 0.006853
204 No Content
```




# User Package

Used by a client to book classes

## Get All


### Request

#### Endpoint

```plaintext
GET /api/user_packages
Origin: http://bauch-thompson-and-jast.mgrapp.com
Authorization: Bearer b28b54a8-54e9-441d-8568-76b876934897
Host: example.org
Cookie: 
```

`GET /api/user_packages`

#### Parameters



| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| active  | Filter by unexpired packages with non-zero sessions remaining (only|_null_) |
| shareable  | Filter by packages that can be shared with other users (only|exclude) |
| recurring  | Filter by recurring packages (only|exclude) |
| resource_offering_id  | Filter packages by applicability to given offering |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;8410db9785c4320ed3d0911c5b3d2314&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 1f406245-f1a1-4885-941e-d6b8d8618a9b
X-Runtime: 0.019424
Content-Length: 2401
200 OK
```


```json
{
  "packages": [
    {
      "id": "fa4f282c-f60f-4248-8408-b4b0759f2bf1",
      "name": "Subsync Tag Receiver",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2018-12-30T17:52:18.562Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "a491601d-f065-4adb-b41b-3640efd6c92e",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-30T17:52:18.525Z",
          "email": "sana@leannon.com",
          "first_name": "Tempie",
          "last_name": "Dickinson",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-30"
        }
      ]
    },
    {
      "id": "84eab1e4-ff29-4162-8541-b025b5241fd2",
      "name": "TAB Remote Gel Adapter",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2018-12-30T17:52:18.557Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "a491601d-f065-4adb-b41b-3640efd6c92e",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-30T17:52:18.525Z",
          "email": "sana@leannon.com",
          "first_name": "Tempie",
          "last_name": "Dickinson",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-30"
        }
      ]
    },
    {
      "id": "832eade7-b460-46a2-9a02-e82a63582ee8",
      "name": "Pientfunc Gel Adapter",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2018-12-30T17:52:18.551Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "a491601d-f065-4adb-b41b-3640efd6c92e",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-30T17:52:18.525Z",
          "email": "sana@leannon.com",
          "first_name": "Tempie",
          "last_name": "Dickinson",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-30"
        }
      ]
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 3,
    "per_page": 100
  }
}
```



# User Transactions

Record of user debits, credits, account balance adjustments, etc. Basically anything that involves a change in money

## Get All


### Request

#### Endpoint

```plaintext
GET /api/transactions
Origin: http://reilly-inc.mgrapp.com
Authorization: Bearer 00e43a41-c4df-49d8-b321-4d6fed034ea8
Host: example.org
Cookie: 
```

`GET /api/transactions`

#### Parameters



| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| start_date  | Filter by Start Date |
| end_date  | Filter by End Date |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
ETag: W/&quot;fa3214aa452aa4cac7f9a6e3b4c4182f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5715cc4f-cd74-45f1-9316-b826a5a8be95
X-Runtime: 0.011528
Content-Length: 2605
200 OK
```


```json
{
  "transactions": [
    {
      "id": "0a597d25-5821-4d96-9577-9faa2a7ecf62",
      "created_at": "2018-12-30T17:52:18.634Z",
      "state": "pending_capture",
      "amount": "15.0",
      "fail_message": null,
      "process_after": null,
      "processed_at": null,
      "payment_type": "account_balance",
      "description": null,
      "payment_source_invalid": false,
      "payment_method": {
        "id": 0,
        "source_id": null,
        "payment_type": "account_balance",
        "brand": null,
        "exp_month": null,
        "exp_year": null,
        "last4": null,
        "balance": "0.0",
        "is_default": null
      },
      "transactable": null,
      "creator_type": null,
      "creator": null
    },
    {
      "id": "ce629d3f-2562-44aa-a769-b4d4df1ff72b",
      "created_at": "2018-12-30T17:52:18.632Z",
      "state": "pending_capture",
      "amount": "21.0",
      "fail_message": null,
      "process_after": null,
      "processed_at": null,
      "payment_type": "account_balance",
      "description": null,
      "payment_source_invalid": false,
      "payment_method": {
        "id": 0,
        "source_id": null,
        "payment_type": "account_balance",
        "brand": null,
        "exp_month": null,
        "exp_year": null,
        "last4": null,
        "balance": "0.0",
        "is_default": null
      },
      "transactable": null,
      "creator_type": null,
      "creator": null
    },
    {
      "id": "e3e65688-18f1-4310-bf60-bea5c6c89be7",
      "created_at": "2018-12-30T17:52:18.630Z",
      "state": "pending_capture",
      "amount": "39.0",
      "fail_message": null,
      "process_after": null,
      "processed_at": null,
      "payment_type": "account_balance",
      "description": null,
      "payment_source_invalid": false,
      "payment_method": {
        "id": 0,
        "source_id": null,
        "payment_type": "account_balance",
        "brand": null,
        "exp_month": null,
        "exp_year": null,
        "last4": null,
        "balance": "0.0",
        "is_default": null
      },
      "transactable": null,
      "creator_type": null,
      "creator": null
    },
    {
      "id": "01fd416a-1b4f-4045-8788-ffba57dceb60",
      "created_at": "2018-12-30T17:52:18.628Z",
      "state": "pending_capture",
      "amount": "71.0",
      "fail_message": null,
      "process_after": null,
      "processed_at": null,
      "payment_type": "account_balance",
      "description": null,
      "payment_source_invalid": false,
      "payment_method": {
        "id": 0,
        "source_id": null,
        "payment_type": "account_balance",
        "brand": null,
        "exp_month": null,
        "exp_year": null,
        "last4": null,
        "balance": "0.0",
        "is_default": null
      },
      "transactable": null,
      "creator_type": null,
      "creator": null
    },
    {
      "id": "cfd327df-5fa2-4105-8263-beaa34379e7b",
      "created_at": "2018-12-30T17:52:18.626Z",
      "state": "pending_capture",
      "amount": "36.0",
      "fail_message": null,
      "process_after": null,
      "processed_at": null,
      "payment_type": "account_balance",
      "description": null,
      "payment_source_invalid": false,
      "payment_method": {
        "id": 0,
        "source_id": null,
        "payment_type": "account_balance",
        "brand": null,
        "exp_month": null,
        "exp_year": null,
        "last4": null,
        "balance": "0.0",
        "is_default": null
      },
      "transactable": null,
      "creator_type": null,
      "creator": null
    }
  ],
  "pagination": {
    "curr_page": 1,
    "next_page": null,
    "prev_page": null,
    "max_page": 1,
    "total_count": 5,
    "per_page": 100
  }
}
```



