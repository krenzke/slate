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
Origin: http://douglas.info
Host: example.org
Cookie: 
```

`GET /api/business_accounts/current`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;75e89d56b85731b1bb84008c0d89bbbf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0b7aa12a-1450-40d1-a95d-dde1d0146830
X-Runtime: 0.011847
Content-Length: 1760
200 OK
```


```json
{
  "business_account": {
    "id": "e0851947-389a-4618-9a85-90203984c5f2",
    "name": "Welch, Waters and O'Reilly",
    "slug": "welch-waters-and-o-reilly",
    "business_type": "fitness_studio",
    "account_type": null,
    "requires_waiver": true,
    "waiver_text": null,
    "waiver_url": null,
    "default_time_zone": "America/Los_Angeles",
    "schedule_release_type": "monthly",
    "schedule_release_day": 20,
    "schedule_release_time": "12:00am",
    "locations": [
      {
        "id": "c461dee9-e26d-412a-85fa-655ee126b830",
        "name": "Mueller-Dare",
        "slug": "mueller-dare",
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
        "reservations_open_until": "2019-03-31T23:59:00.000-07:00",
        "next_schedule_release_at": "2019-03-20T00:00:00.000-07:00",
        "allow_guest_only_reservations": true,
        "show_waitlist_capacity": true,
        "default_schedule_display_period": null
      },
      {
        "id": "1d7c6a9e-b460-4bb9-a155-67bcdbe626d9",
        "name": "Schaden and Sons",
        "slug": "schaden-and-sons",
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
        "reservations_open_until": "2019-03-31T23:59:00.000-07:00",
        "next_schedule_release_at": "2019-03-20T00:00:00.000-07:00",
        "allow_guest_only_reservations": true,
        "show_waitlist_capacity": true,
        "default_schedule_display_period": null
      }
    ],
    "roles": [
      {
        "id": "c46b65e3-8eee-4b53-bd83-9bcc86078577",
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
        "id": "296ec875-6009-43c5-9986-10dd359191e7",
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
Origin: http://feil-heaney.mgrapp.com
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
ETag: W/&quot;6fbdedfa35f5a2da624126e597c4f64c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0de88efd-1488-4ef5-ae0c-868144735a69
X-Runtime: 0.043144
Content-Length: 1107
200 OK
```


```json
{
  "business_staffs": [
    {
      "id": "58bd5921-c8de-433f-8bf5-5ac14523de2a",
      "email": "leila.lebsack@harveylabadie.info",
      "slug": "jule-torphy",
      "first_name": "Jule",
      "last_name": "Torphy",
      "description": null,
      "hire_date": null,
      "phone": null,
      "is_kiosk": false,
      "profile_image": null,
      "roles": [
        {
          "id": "9482734c-4dc6-4ef4-bce3-e377883ee644",
          "role_id": "78373416-ae9e-4b3e-8277-18a095af39cf",
          "name": "Instructor",
          "slug": "instructor"
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
      "id": "4753962b-73d1-455f-b2a1-2d5b618bb526",
      "email": "belle@wizamurazik.co.uk",
      "slug": "malena-parisian",
      "first_name": "Malena",
      "last_name": "Parisian",
      "description": null,
      "hire_date": null,
      "phone": null,
      "is_kiosk": false,
      "profile_image": null,
      "roles": [
        {
          "id": "01f323e3-a4c4-4fe2-b908-6844c23d54d6",
          "role_id": "78373416-ae9e-4b3e-8277-18a095af39cf",
          "name": "Instructor",
          "slug": "instructor"
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
Origin: http://herman-and-sons.mgrapp.com
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
ETag: W/&quot;d7546f04025d4f116dc03cd70e26278c&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 94c73115-b72c-49e2-ad0d-6f1e0ca81b38
X-Runtime: 0.042564
Content-Length: 1686
200 OK
```


```json
{
  "business_staffs": [
    {
      "id": "32ff21a5-4659-4e5a-81ab-057a05eacbc5",
      "email": "janella@conroy.info",
      "slug": "adelle-considine",
      "first_name": "Adelle",
      "last_name": "Considine",
      "description": null,
      "hire_date": null,
      "phone": null,
      "is_kiosk": false,
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
      "id": "f7c2cf5a-eb0f-4be3-8cc9-f45d3e489afd",
      "email": "nakesha@purdy.co.uk",
      "slug": "sharolyn-wehner",
      "first_name": "Sharolyn",
      "last_name": "Wehner",
      "description": null,
      "hire_date": null,
      "phone": null,
      "is_kiosk": false,
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
      "id": "7d829c5a-93f2-4160-bc7c-717ea906ba4e",
      "email": "marvin@zboncak.name",
      "slug": "lakita-jerde",
      "first_name": "Lakita",
      "last_name": "Jerde",
      "description": null,
      "hire_date": null,
      "phone": null,
      "is_kiosk": false,
      "profile_image": null,
      "roles": [
        {
          "id": "229cdfb2-ce82-4080-a883-507069f5439d",
          "role_id": "4d2f2838-bceb-43c6-9787-47e0df6593e8",
          "name": "Instructor",
          "slug": "instructor"
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
      "id": "2d8c1a0d-bcc1-43c9-ac61-f8694e9582f2",
      "email": "shante@jacobson.biz",
      "slug": "thelma-huel",
      "first_name": "Thelma",
      "last_name": "Huel",
      "description": null,
      "hire_date": null,
      "phone": null,
      "is_kiosk": false,
      "profile_image": null,
      "roles": [
        {
          "id": "887b1e62-937d-420a-93c0-bae41634e93d",
          "role_id": "4d2f2838-bceb-43c6-9787-47e0df6593e8",
          "name": "Instructor",
          "slug": "instructor"
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
Origin: http://crona-ryan.mgrapp.com
Authorization: Bearer e3fe5e56-66a2-42e1-9cdc-d41c18528540
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/gift_cards/redeem`

#### Parameters


```json
code=5A0B81D7
```


| Name | Description |
|:-----|:------------|
| code *required* | Gift Card Code |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c294096f0c195384bbb4b5d72d6e7f90&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 57c7cf27-f5f6-4722-a041-17c30134743c
X-Runtime: 0.059344
Content-Length: 1291
201 Created
```


```json
{
  "gift_card_instance": {
    "id": "976763aa-5e20-48a2-bb71-e11fc13abcef",
    "gift_card_type": "cash",
    "amount": "22.0",
    "code": "5A0B81D7",
    "num_sessions": 0,
    "created_at": "2019-03-13T18:33:01.817Z",
    "redeemed_at": "2019-03-13T18:33:01.849Z",
    "redeemer": {
      "email": "loreta_thiel@toybreitenberg.info"
    }
  },
  "transaction": {
    "id": "4912620c-6c14-415d-a90b-973fcd52085e",
    "created_at": "2019-03-13T18:33:01.860Z",
    "state": "complete",
    "amount": "-22.0",
    "fail_message": null,
    "process_after": null,
    "processed_at": "2019-03-13T18:33:01.872Z",
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
      "balance": "122.0",
      "is_default": null
    },
    "transactable": null,
    "creator_type": null,
    "creator": null
  },
  "package_instance": null,
  "user_profile": {
    "id": "2b8917a8-74f1-4750-9f05-739717179920",
    "account_balance": "122.0",
    "signed_waiver_at": null,
    "created_at": "2019-03-13T18:33:01.828Z",
    "email": "loreta_thiel@toybreitenberg.info",
    "first_name": "Brady",
    "last_name": "Deckow",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2019-03-13",
    "password_reset_required": false,
    "emergency_contact_name": null,
    "emergency_contact_phone": null
  }
}
```



# Offerings

Specific instances of a class that a user can sign up for

## Filter By Location


### Request

#### Endpoint

```plaintext
GET /api/offerings?time_zone_offset=420&amp;location_id=db360552-8021-4984-8740-2fcc0fc59bd8
Origin: http://bernier-hayes.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/offerings`

#### Parameters


```json
time_zone_offset: 420
location_id: db360552-8021-4984-8740-2fcc0fc59bd8
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
ETag: W/&quot;54e67b5f18ab51df80032744ffb2e4cd&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 532c77f8-9167-4a9c-bb04-854bdd2e7e1e
X-Runtime: 0.012841
Content-Length: 4600
200 OK
```


```json
{
  "offerings": [
    {
      "id": "3daec2af-c044-49fa-8a6e-d27a58cc213e",
      "name": "Dutch Goats 0c6dc4f2",
      "resource_id": "e145a5b0-471a-48f3-9284-4661f72072cf",
      "resource_slug": "dutch-goats-0c6dc4f2",
      "recurrence_id": null,
      "state": "active",
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
      "num_normal_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Corkery Inc",
      "location_id": "db360552-8021-4984-8740-2fcc0fc59bd8",
      "description": "Coagulation of the milk protein casein so cute but cheesy New York cheesecake harmful secondary metabolites - tongue in cheek taste and texture in all colours the whiter and fresher the cheese, the crisper and fruitier the wine should be cut to size blue fungi in cream a good alternative to cheesecloth.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "abcbbdc4-cabb-4248-93ad-2fcfcdaa8095",
        "email": "antonia.balistreri@dooleybeier.biz",
        "slug": "elicia-farrell",
        "first_name": "Elicia",
        "last_name": "Farrell",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
    },
    {
      "id": "43f5bb31-2594-4758-9c1d-0cbe026a84a9",
      "name": "Melting Affineurs 25574313",
      "resource_id": "8a7caab2-287c-4c58-a13f-c2da8e27c3c2",
      "resource_slug": "melting-affineurs-25574313",
      "recurrence_id": null,
      "state": "active",
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
      "num_normal_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Corkery Inc",
      "location_id": "db360552-8021-4984-8740-2fcc0fc59bd8",
      "description": "They can also age quite well in ripening cellars where cheese paring with wine cut the cheese salt, pepper, mustard and vinegar harmful secondary metabolites of cheesy business lingo of cheesy business lingo salt, pepper, mustard and vinegar so cute but cheesy blue fungi in cream.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "3d95aa46-7e5d-4714-b6ef-2b7935a441ab",
        "email": "marylin@langoshziemann.info",
        "slug": "donnell-wintheiser",
        "first_name": "Donnell",
        "last_name": "Wintheiser",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
    },
    {
      "id": "5f11144d-d8a2-4cba-a3c0-ac9523ba7003",
      "name": "Dutch Goats 0c6dc4f2",
      "resource_id": "e145a5b0-471a-48f3-9284-4661f72072cf",
      "resource_slug": "dutch-goats-0c6dc4f2",
      "recurrence_id": null,
      "state": "active",
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
      "num_normal_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Corkery Inc",
      "location_id": "db360552-8021-4984-8740-2fcc0fc59bd8",
      "description": "Coagulation of the milk protein casein so cute but cheesy New York cheesecake harmful secondary metabolites - tongue in cheek taste and texture in all colours the whiter and fresher the cheese, the crisper and fruitier the wine should be cut to size blue fungi in cream a good alternative to cheesecloth.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "6569e8f5-ed2d-408c-9bab-daaafc7e8554",
        "email": "clora.fahey@wisozk.com",
        "slug": "larita-stracke",
        "first_name": "Larita",
        "last_name": "Stracke",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
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
Origin: http://beer-kirlin-and-braun.mgrapp.com
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
ETag: W/&quot;022de7e60cf5c5aa8cf29385716b3730&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: cccd38e7-ce04-4a3f-8432-fcc429f685dc
X-Runtime: 0.022779
Content-Length: 4482
200 OK
```


```json
{
  "offerings": [
    {
      "id": "d16d95c5-7074-4b97-a2ca-217a144a9abc",
      "name": "Grated Affineurs d0c68430",
      "resource_id": "70762b3c-debb-456f-9598-b4148cd34eb9",
      "resource_slug": "grated-affineurs-d0c68430",
      "recurrence_id": null,
      "state": "active",
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
      "num_normal_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Jaskolski, Terry and Luettgen",
      "location_id": "b65f7cd5-28ae-4b2b-8a88-de1f59f1c7c5",
      "description": "Cheeseparing blessed are the cheesemakers soft ripening cheese for so cute but cheesy wash, rinse, repeat harmful secondary metabolites trying too hard, unsubtle, and inauthentic so cute but cheesy - tongue in cheek separate the curds from the wey.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "150e875b-1302-443e-a6b7-75a0533bffdd",
        "email": "madeleine_rempel@vandervort.biz",
        "slug": "louis-harris",
        "first_name": "Louis",
        "last_name": "Harris",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
    },
    {
      "id": "67671bdf-b64e-45a6-9d25-76332b89d7e0",
      "name": "Grated Sheep 7a32c5be",
      "resource_id": "3db4d07e-3b3d-421c-841b-6c5edc9fe0fb",
      "resource_slug": "grated-sheep-7a32c5be",
      "recurrence_id": null,
      "state": "active",
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
      "num_normal_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Jaskolski, Terry and Luettgen",
      "location_id": "b65f7cd5-28ae-4b2b-8a88-de1f59f1c7c5",
      "description": "Penicillium roqueforti the milky way of they were so cheesed off team cheesy says hi double dutch or double dutch or - tongue in cheek salt, pepper, mustard and vinegar blue fungi in cream is like chalk and cheese.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "3ae08d3b-4b4f-4079-90cf-2a69d43c1b30",
        "email": "sherwood_stehr@medhursteichmann.com",
        "slug": "joesph-roob",
        "first_name": "Joesph",
        "last_name": "Roob",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
    },
    {
      "id": "23b15b2f-5ae7-4e6d-ab61-f20de3a9dd3d",
      "name": "Grated Affineurs d0c68430",
      "resource_id": "70762b3c-debb-456f-9598-b4148cd34eb9",
      "resource_slug": "grated-affineurs-d0c68430",
      "recurrence_id": null,
      "state": "active",
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
      "num_normal_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Jaskolski, Terry and Luettgen",
      "location_id": "b65f7cd5-28ae-4b2b-8a88-de1f59f1c7c5",
      "description": "Cheeseparing blessed are the cheesemakers soft ripening cheese for so cute but cheesy wash, rinse, repeat harmful secondary metabolites trying too hard, unsubtle, and inauthentic so cute but cheesy - tongue in cheek separate the curds from the wey.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "ea6ca0a1-8d8f-4c2d-9199-007cbdc773dd",
        "email": "glenda_breitenberg@baumbach.name",
        "slug": "royal-botsford",
        "first_name": "Royal",
        "last_name": "Botsford",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
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
Origin: http://collier-inc.mgrapp.com
Authorization: Bearer 2ee2a92e-5a12-4f0e-8f9c-bf985064acce
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders`

#### Parameters


```json
line_items[][variant_id]=188847ad-9a4f-4f6e-8f99-c4f21829d229&line_items[][quantity]=1&payments[][payment_type]=stripe_cc&payments[][source_id]=test_cc_2
```


| Name | Description |
|:-----|:------------|
| line_items *required* | List of items ({variant_id:, quantity:}) |
| payments *required* | List of payments ({payment_type:, source_id:}) |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;fb0363f45410fe8f68d311d37756e27d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 209d14eb-c408-47c4-aa2f-fa0e661af2a3
X-Runtime: 0.150319
Content-Length: 1505
201 Created
```


```json
{
  "order": {
    "id": "ce9d5888-70a4-4908-bedb-6352127f9854",
    "number": "ce9d5888",
    "line_items": [
      {
        "id": "4f21bc83-3410-4612-91c1-123929870307",
        "quantity": 1,
        "per_unit_price": "74.0",
        "name": "Pountfunc Side Audible System",
        "variant": {
          "id": "188847ad-9a4f-4f6e-8f99-c4f21829d229",
          "price": "74.0",
          "is_master": true
        }
      }
    ],
    "created_at": "2019-03-13T18:33:02.553Z",
    "total": "0.0",
    "item_total": "74.0",
    "adjustment_total": "0.0",
    "payment_total": "74.0",
    "payment_state": "complete",
    "fulfillment_state": "complete",
    "user": {
      "id": "cd137fca-c601-4b4c-b709-90355cb99be5",
      "account_balance": "0.0",
      "signed_waiver_at": null,
      "created_at": "2019-03-13T18:33:02.444Z",
      "email": "pilar_auer@reinger.ca",
      "first_name": "Marla",
      "last_name": "Heller",
      "address1": null,
      "address2": null,
      "city": null,
      "state": null,
      "zip_code": null,
      "phone": null,
      "dob": null,
      "member_start_date": "2019-03-13",
      "password_reset_required": false,
      "emergency_contact_name": null,
      "emergency_contact_phone": null
    },
    "payments": [
      {
        "id": "8840a456-3b19-4840-b351-1342a3bfd6a0",
        "created_at": "2019-03-13T18:33:02.570Z",
        "state": "complete",
        "amount": "74.0",
        "fail_message": null,
        "process_after": null,
        "processed_at": "2019-03-13T18:33:02.608Z",
        "payment_type": "stripe_cc",
        "description": null,
        "payment_source_invalid": false,
        "payment_method": null,
        "transactable": {
          "type": "order",
          "id": "ce9d5888-70a4-4908-bedb-6352127f9854",
          "number": "ce9d5888",
          "total": "0.0",
          "item_total": "74.0",
          "adjustment_total": "0.0",
          "payment_total": "74.0",
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
Origin: http://von-and-sons.mgrapp.com
Authorization: Bearer 70f7939e-d34d-4dc1-bf41-6504105612ed
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
ETag: W/&quot;02eda27274dacb5d255f29524466cc3f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e089a144-e101-4993-aeeb-7e743094a7e6
X-Runtime: 0.025343
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
Origin: http://kovacek-inc.mgrapp.com
Authorization: Bearer 6bb08ea0-9ccc-439f-9a02-735b34d84d3c
Host: example.org
Cookie: 
```

`GET /api/payment_methods`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;7216d8771b3dc03ea716050a31fed360&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 3ecb1865-e723-42a7-93e9-b5a3f2dc1305
X-Runtime: 0.007456
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
GET /api/products?types[]=package
Origin: http://barton-group.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/products`

#### Parameters


```json
types: [&quot;package&quot;]
```


| Name | Description |
|:-----|:------------|
| page  | Page |
| per_page  | Per Page |
| q  | Search by Name |
| types  | Filter by Product Type |
| resource_offering_id  | Filter packages by applicability to given offering |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;6dabcce5b728736c579c6887077b3ce8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9c862693-da8d-432c-a263-bf28d5862298
X-Runtime: 0.014522
Content-Length: 1749
200 OK
```


```json
{
  "products": [
    {
      "id": "0766ade6-f912-4674-bcf7-d06a8998ca4b",
      "name": "Phienceforge Auto Amplifier",
      "slug": "phienceforge-auto-amplifier",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "4a2fc548-ea37-4c3b-b30c-657733cb2d6e",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "advance_schedule_in_days": null,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "waitlist_priority": 1
      },
      "gift_card": null,
      "challenge_entry": null,
      "variants": [
        {
          "id": "fefb5b73-3d9b-46c6-a52d-2ebdac51c6ee",
          "price": "22.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "22.0",
      "image": null
    },
    {
      "id": "e0067af1-bfd9-4e83-a08b-fd3bbea2b669",
      "name": "Phienewood Direct Kit",
      "slug": "phienewood-direct-kit",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "7f8af95f-0c5e-405f-8d20-c10d2acf2482",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "advance_schedule_in_days": null,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "waitlist_priority": 1
      },
      "gift_card": null,
      "challenge_entry": null,
      "variants": [
        {
          "id": "c9d8fc18-09f0-4b84-a5a5-a51e4c8246dd",
          "price": "76.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "76.0",
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
Origin: http://bartoletti-and-sons.mgrapp.com
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
| types  | Filter by Product Type |
| resource_offering_id  | Filter packages by applicability to given offering |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;1ef347be831f527bd4ff0b9b247aac02&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 463b3d01-e6c9-4a2c-80e8-4a0abbea7b32
X-Runtime: 0.097222
Content-Length: 3021
200 OK
```


```json
{
  "products": [
    {
      "id": "e2b7e92c-cca8-4b18-bb49-3b759d76d499",
      "name": "Sinebalt Remote Portable System",
      "slug": "sinebalt-remote-portable-system",
      "description": null,
      "product_type": "gift_card",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": {
        "id": "aded9f01-80da-4f13-8ab2-0149f70cb9b3",
        "gift_card_type": "cash",
        "fixed_amount": true,
        "amount": "20.0",
        "num_sessions": 0
      },
      "challenge_entry": null,
      "variants": [
        {
          "id": "4c87e468-8f64-42cb-a896-ac74438bcb95",
          "price": "9.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "9.0",
      "image": null
    },
    {
      "id": "5cecdce9-29ad-4fd1-8538-1a353b232551",
      "name": "MIF Electric Kit",
      "slug": "mif-electric-kit",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "1f1b061f-0ab4-4183-9505-68d1a46e3fbd",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "advance_schedule_in_days": null,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "waitlist_priority": 1
      },
      "gift_card": null,
      "challenge_entry": null,
      "variants": [
        {
          "id": "bb27ea10-a275-4b28-a867-5096fd7f222d",
          "price": "33.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "33.0",
      "image": null
    },
    {
      "id": "2224f91f-14ca-4e00-b836-f80d06593256",
      "name": "Brure Video Compressor",
      "slug": "brure-video-compressor",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "dba601ef-5048-43ce-a4df-43e6fb522275",
        "unlimited_sessions": false,
        "num_sessions": 10,
        "expiration_type": "none",
        "expiration_time_in_days": 0,
        "redemption_limit_type": "none",
        "redemption_limit_value": 0,
        "advance_schedule_in_days": null,
        "shareable": false,
        "for_guest_only": false,
        "guests_allowed": true,
        "recurrence_type": null,
        "recurrence_unit": null,
        "recurrence_period": null,
        "is_recurring": false,
        "recurring_price": "0.0",
        "waitlist_priority": 1
      },
      "gift_card": null,
      "challenge_entry": null,
      "variants": [
        {
          "id": "7f62204b-b1dd-4698-87e9-377fe41a0f1a",
          "price": "16.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "16.0",
      "image": null
    },
    {
      "id": "6c2fb832-d21f-46e9-a1d1-aabb28fdc194",
      "name": "Lunix HD Portable Filter",
      "slug": "lunix-hd-portable-filter",
      "description": null,
      "product_type": "normal",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": null,
      "challenge_entry": null,
      "variants": [
        {
          "id": "7a023420-3229-45db-9238-4be6f808c6f8",
          "price": "38.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "38.0",
      "image": null
    },
    {
      "id": "7dc0d377-bd3a-4a6b-8fb8-4b6860346a21",
      "name": "Phounewood Output Transmitter",
      "slug": "phounewood-output-transmitter",
      "description": null,
      "product_type": "normal",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": null,
      "challenge_entry": null,
      "variants": [
        {
          "id": "71be93b9-0d47-48c2-894a-19658d8b9335",
          "price": "74.0",
          "is_master": true
        }
      ],
      "perks": [

      ],
      "price": "74.0",
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
Origin: http://swift-jenkins.mgrapp.com
Authorization: Bearer cd1189fe-1cd6-4ded-b73b-4c3916478eea
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/reservations`

#### Parameters


```json
reservations[][resource_offering_id]=2d8b0be4-bb47-449d-bb4a-13e384c0dd05&reservations[][package_instance_id]=04a5722d-20ab-4145-8496-c9f1268d2148
```


| Name | Description |
|:-----|:------------|
| reservations[resource_offering_id] *required* | Id of offering to sign up for |
| reservations[package_instance_id] *required* | Id of package used to pay for reservation |
| reservations[is_guest]  | Reservation is for a guest? |
| reservations[guest_name]  | Guest Name |
| reservations[guest_email]  | Guest Email |
| reservations[guest_phone]  | Guest Phone |
| reservations[accepts_waiver]  | If user accepts waiver |
| reservations[note]  | Note to the instructor |
| reservations[recurrence][start_date]  | Recurrence Start Date |
| reservations[recurrence][end_date]  | Recurrence End Date |
| reservations[recurrence][on_monday]  | Include Monday recurrences |
| reservations[recurrence][on_tuesday]  | Include Tuesday recurrences |
| reservations[recurrence][on_wednesday]  | Include Wednesday recurrences |
| reservations[recurrence][on_thursday]  | Include Thursday recurrences |
| reservations[recurrence][on_friday]  | Include Friday recurrences |
| reservations[recurrence][on_saturday]  | Include Saturday recurrences |
| reservations[recurrence][on_sunday]  | Include Sunday recurrences |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;dfdbbd4159c1a9d9bc83ff6d11cc9a6f&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 9d461f40-cd83-4649-a777-77263b67b673
X-Runtime: 0.096296
Content-Length: 2844
201 Created
```


```json
{
  "reservations": [
    {
      "id": "d36579c0-a4ef-4f5c-b8b3-d0b13df49251",
      "state": "reserved",
      "created_at": "2019-03-13T18:33:01.388Z",
      "cancelled_at": null,
      "offering_id": "2d8b0be4-bb47-449d-bb4a-13e384c0dd05",
      "package_instance_id": "04a5722d-20ab-4145-8496-c9f1268d2148",
      "is_guest": false,
      "time_zone": "America/Los_Angeles",
      "start_time": "2019-03-13T19:33:01.269Z",
      "waitlist_promoted_at": null,
      "signed_in_at": null,
      "resource_name": "Sharp Sheep f611ec9d"
    }
  ],
  "offerings": [
    {
      "id": "2d8b0be4-bb47-449d-bb4a-13e384c0dd05",
      "name": "Sharp Sheep f611ec9d",
      "resource_id": "495c5856-7e38-4be3-90f7-290c2a018819",
      "resource_slug": "sharp-sheep-f611ec9d",
      "recurrence_id": null,
      "state": "active",
      "start_time": "2019-03-13T19:33:01.269Z",
      "end_time": "2019-03-13T20:33:01.269Z",
      "reservation_cutoff_time": "2019-03-13T19:33:01.269Z",
      "reservation_cutoff_time_in_minutes": 0,
      "waitlist_cutoff_time": "2019-03-13T19:33:01.269Z",
      "waitlist_cutoff_time_in_minutes": 0,
      "late_cancel_cutoff_time": "2019-03-13T19:33:01.269Z",
      "late_cancel_cutoff_time_in_minutes": 0,
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 10,
      "num_normal_reservations": 1,
      "time_zone": "America/Los_Angeles",
      "location_name": "Mraz-Reynolds",
      "location_id": "f23b3394-ea76-4d1c-90e1-b546fe3c402d",
      "description": "Sheridans cheesemongers is like chalk and cheese applewood smoked trying too hard, unsubtle, and inauthentic harmful secondary metabolites team cheesy says hi of cheesy business lingo until the wheels form a white coat of penicillium moulds blessed are the cheesemakers harmful secondary metabolites.",
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "provider": {
        "id": "9a3fe3f9-c70e-4a45-8c4e-3bf5d44fcfac",
        "email": "lorie@jakubowskimante.biz",
        "slug": "leta-haley",
        "first_name": "Leta",
        "last_name": "Haley",
        "description": null,
        "hire_date": null,
        "phone": null,
        "is_kiosk": false,
        "profile_image": null
      },
      "substitute": null
    }
  ],
  "packages": [
    {
      "id": "04a5722d-20ab-4145-8496-c9f1268d2148",
      "name": "Aftersync Gel Transmitter",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 10,
      "sessions_remaining": 10,
      "created_at": "2019-03-13T18:33:01.124Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "advance_schedule_in_days": null,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "ea284658-5850-483c-a6a5-7794cec5501f",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2019-03-13T18:33:01.149Z",
          "email": "na.schulist@pagac.ca",
          "first_name": "Melina",
          "last_name": "Kreiger",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2019-03-13",
          "password_reset_required": false,
          "emergency_contact_name": null,
          "emergency_contact_phone": null
        }
      ]
    }
  ],
  "missing": [

  ]
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
Origin: http://schiller-kihn-and-braun.mgrapp.com
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
ETag: W/&quot;b8e9d045dce10bbefcb6c3f7c0e89f27&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 40babbea-de9e-4df0-a5ce-e514ec4d7d16
X-Runtime: 0.016796
Content-Length: 1929
200 OK
```


```json
{
  "resources": [
    {
      "id": "a154b01d-2baf-42e4-9c1f-130ff1e7e5a0",
      "name": "Melting Alpine a27ab788",
      "slug": "melting-alpine-a27ab788",
      "description": "The slice of cheese is placed on top of the meat patty blue fungi in cream is like chalk and cheese but don't you agree? It is no use crying over spilled milk the sticky nature of processed cheese can make it difficult to slice, but cut the cheese the whiter and fresher the cheese, the crisper and fruitier the wine should be when the rennet is added, curds are formed with Dutch courage dutch sandwich.",
      "resource_type": null,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "image": null
    },
    {
      "id": "23f7e664-b680-4910-a070-fa1b29266e8e",
      "name": "Milky Goats 11de5da1",
      "slug": "milky-goats-11de5da1",
      "description": "The early bird may get the worm, but the second mouse gets the cheese in the trap but round cheeses are to be cut in wedges, like a cake is like chalk and cheese say cheese blessed are the cheesemakers blue fungi in cream they were so cheesed off dutch sandwich blend the flour, cheese and is like chalk and cheese.",
      "resource_type": null,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "image": null
    },
    {
      "id": "2d10ace6-e249-4f02-a763-fe56a724ba88",
      "name": "Nutty Brie fd583955",
      "slug": "nutty-brie-fd583955",
      "description": "The early bird may get the worm, but the second mouse gets the cheese in the trap bergkäse from the Alps when the rennet is added, curds are formed but round cheeses are to be cut in wedges, like a cake they can also age quite well in ripening cellars where blessed are the cheesemakers the whiter and fresher the cheese, the crisper and fruitier the wine should be soft ripening cheese for cheeseparing so cute but cheesy.",
      "resource_type": null,
      "pre_reservation_message": null,
      "post_reservation_message": null,
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

## Check Email


### Request

#### Endpoint

```plaintext
GET /api/users/check_email?email=darcie_senger%40nolan.ca
Origin: http://barton-dibbert-and-zieme.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/users/check_email`

#### Parameters


```json
email: darcie_senger@nolan.ca
```


| Name | Description |
|:-----|:------------|
| email *required* | Email |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c821f1244fd68b10cc644a392beaf4d8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d0d35aa2-0d46-4636-9e2d-e02516bfff07
X-Runtime: 0.007655
Content-Length: 34
200 OK
```


```json
{
  "exists": true,
  "phone_last4": null
}
```



## Get Session


### Request

#### Endpoint

```plaintext
GET /api/users/me
Origin: http://becker-koelpin-and-ebert.mgrapp.com
Authorization: Bearer 88144ab6-f17a-4bdb-8caf-662b816aaf20
Host: example.org
Cookie: 
```

`GET /api/users/me`

#### Parameters


None known.


### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;7f01e73ca04534c594390a2a16f00198&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 2172a9db-a752-4e0b-ba34-0d6a9242e2e4
X-Runtime: 0.006883
Content-Length: 536
200 OK
```


```json
{
  "session": {
    "id": "88144ab6-f17a-4bdb-8caf-662b816aaf20",
    "expires_at": "2019-03-27T18:33:02.051Z"
  },
  "user": {
    "id": "7e243142-10e0-4dca-bf70-edb256680549",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2019-03-13T18:33:02.049Z",
    "email": "tommie_abbott@mraz.biz",
    "first_name": "Kristal",
    "last_name": "Kris",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2019-03-13",
    "password_reset_required": false,
    "emergency_contact_name": null,
    "emergency_contact_phone": null
  }
}
```



## Register


### Request

#### Endpoint

```plaintext
POST /api/users
Origin: http://kris-stoltenberg-and-hirthe.mgrapp.com
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
ETag: W/&quot;43c104a51da88b457b4d67c4fc355bb6&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 38fc21f0-a219-4431-8dea-e36824569817
X-Runtime: 0.030786
Content-Length: 551
201 Created
```


```json
{
  "session": {
    "id": "d60a270c-7aa1-456c-b5b2-af17518eada3",
    "expires_at": null
  },
  "user": {
    "id": "903a709b-3920-43e6-b813-0aea69b47333",
    "account_balance": "0.0",
    "signed_waiver_at": "2019-03-13T18:33:02.085Z",
    "created_at": "2019-03-13T18:33:02.093Z",
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
    "member_start_date": "2019-03-13",
    "password_reset_required": false,
    "emergency_contact_name": null,
    "emergency_contact_phone": null
  }
}
```



## Request Password Reset Token


### Request

#### Endpoint

```plaintext
POST /api/users/password_reset_token
Origin: http://schuppe-denesik-and-johnston.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/password_reset_token`

#### Parameters


```json
email=neda%40stehr.com
```


| Name | Description |
|:-----|:------------|
| email *required* | Email |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;44136fa355b3678a1146ad16f7e8649e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 336030c8-1ed5-4d49-b70e-e41a28867aed
X-Runtime: 0.010800
Content-Length: 2
200 OK
```


```json
{
}
```



## Reset Password


### Request

#### Endpoint

```plaintext
POST /api/users/db19993c-d6ed-4c4c-a151-bf5509e84d1f/reset_password
Origin: http://mckenzie-group.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/:user_id/reset_password`

#### Parameters


```json
password=new-password&old_password=password
```


| Name | Description |
|:-----|:------------|
| password *required* | Password Reset Token |
| old_password *required* | Password Reset Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;8667df2de09d480ccbfe0d9a851d1896&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: f56ce367-b15c-4089-b99d-aceefdc0d4a5
X-Runtime: 0.027060
Content-Length: 521
200 OK
```


```json
{
  "session": {
    "id": "f139e9b9-9be9-4222-979e-2eaa9998d48f",
    "expires_at": null
  },
  "user": {
    "id": "db19993c-d6ed-4c4c-a151-bf5509e84d1f",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2019-03-13T18:33:01.952Z",
    "email": "hubert@lednermorissette.biz",
    "first_name": "Reginald",
    "last_name": "Hayes",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2019-03-13",
    "password_reset_required": false,
    "emergency_contact_name": null,
    "emergency_contact_phone": null
  }
}
```



## Send Email Verification Token


### Request

#### Endpoint

```plaintext
POST /api/users/send_email_verification_token
Origin: http://klocko-kub-and-carter.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/send_email_verification_token`

#### Parameters


```json
email=lorriane%40heaney.biz&send_via=email
```


| Name | Description |
|:-----|:------------|
| email *required* | Email |
| send_via *required* | Method to send by ("email" or "sms") |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;44136fa355b3678a1146ad16f7e8649e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 10d6700c-530d-4fa0-86cb-22454cf9b986
X-Runtime: 0.029476
Content-Length: 2
200 OK
```


```json
{
}
```



## Sign In


### Request

#### Endpoint

```plaintext
POST /api/users/session
Origin: http://hoppe-gutmann-and-hayes.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/session`

#### Parameters


```json
email=setsuko%40ziemejast.biz&password=password
```


| Name | Description |
|:-----|:------------|
| email *required* | Email |
| password *required* | Password |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;c8e9c17705dcc027cb208fadfa15b4ca&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a105eabc-a670-4798-9b09-a391d39cb6bb
X-Runtime: 0.009841
Content-Length: 514
201 Created
```


```json
{
  "session": {
    "id": "c7d5fa6f-b63d-4861-a513-d924664aa8e5",
    "expires_at": null
  },
  "user": {
    "id": "0de70fd0-b4cc-4923-8fb1-7a36cf3e1848",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2019-03-13T18:33:02.207Z",
    "email": "setsuko@ziemejast.biz",
    "first_name": "Nancey",
    "last_name": "Harris",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2019-03-13",
    "password_reset_required": false,
    "emergency_contact_name": null,
    "emergency_contact_phone": null
  }
}
```



## Sign Out


### Request

#### Endpoint

```plaintext
DELETE /api/users/session
Origin: http://kessler-paucek-and-schroeder.mgrapp.com
Authorization: Bearer b59e00cf-61a1-4cb1-8e53-3a648748a05b
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
Cache-Control: no-cache
X-Request-Id: 1d044149-6b68-4b55-b2ec-95362d26c19a
X-Runtime: 0.006544
204 No Content
```




## Verify Password Reset Token


### Request

#### Endpoint

```plaintext
GET /api/users/password_reset_token?token=032f33dace4c6a25589ff3cde3604603
Origin: http://schultz-will-and-kessler.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/users/password_reset_token`

#### Parameters


```json
token: 032f33dace4c6a25589ff3cde3604603
```


| Name | Description |
|:-----|:------------|
| token *required* | Password Reset Token |



### Response

```plaintext
Content-Type: application/json; charset=utf-8
ETag: W/&quot;1c51ef8cc8b96ab62c879f389e3bacf3&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 8288a9a7-e7dc-40d2-90f8-e67517d46d97
X-Runtime: 0.013323
Content-Length: 440
200 OK
```


```json
{
  "user": {
    "id": "87cd5b08-c641-4ea1-ab83-2be0daa5dc08",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2019-03-13T18:33:02.017Z",
    "email": "bernie@russelmurazik.us",
    "first_name": "Caryl",
    "last_name": "Robel",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2019-03-13",
    "password_reset_required": false,
    "emergency_contact_name": null,
    "emergency_contact_phone": null
  }
}
```



# User Package

Used by a client to book classes

## Get All


### Request

#### Endpoint

```plaintext
GET /api/user_packages
Origin: http://hudson-douglas.mgrapp.com
Authorization: Bearer f0abdc27-4ec1-48e6-801a-957fe7a4a15a
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
ETag: W/&quot;d4d1497bd958ab3b6493fe1d12ec7a6e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 514b3032-1116-4804-8835-43873f4a7e79
X-Runtime: 0.024382
Content-Length: 2779
200 OK
```


```json
{
  "packages": [
    {
      "id": "26fb821a-2bed-45da-a773-d6b1a13616f0",
      "name": "Cygpod Output System",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2019-03-13T18:33:01.699Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "advance_schedule_in_days": null,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "3609f99d-8de3-4e77-ae40-d1982ecc0620",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2019-03-13T18:33:01.663Z",
          "email": "toby@cronin.co.uk",
          "first_name": "Lamont",
          "last_name": "Spinka",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2019-03-13",
          "password_reset_required": false,
          "emergency_contact_name": null,
          "emergency_contact_phone": null
        }
      ]
    },
    {
      "id": "548e4db3-9a78-46ad-847c-653b051b970b",
      "name": "Phostfunc Electric Output Filter",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2019-03-13T18:33:01.693Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "advance_schedule_in_days": null,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "3609f99d-8de3-4e77-ae40-d1982ecc0620",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2019-03-13T18:33:01.663Z",
          "email": "toby@cronin.co.uk",
          "first_name": "Lamont",
          "last_name": "Spinka",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2019-03-13",
          "password_reset_required": false,
          "emergency_contact_name": null,
          "emergency_contact_phone": null
        }
      ]
    },
    {
      "id": "f358e3d3-740d-49d4-91bc-813487a8bff1",
      "name": "Brunsfunc GPS Viewer",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2019-03-13T18:33:01.687Z",
      "is_recurring": false,
      "shareable": false,
      "guests_allowed": true,
      "for_guest_only": false,
      "waitlist_priority": 1,
      "advance_schedule_in_days": null,
      "recurrence_type": null,
      "recurrence_unit": null,
      "recurrence_period": null,
      "users": [
        {
          "id": "3609f99d-8de3-4e77-ae40-d1982ecc0620",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2019-03-13T18:33:01.663Z",
          "email": "toby@cronin.co.uk",
          "first_name": "Lamont",
          "last_name": "Spinka",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2019-03-13",
          "password_reset_required": false,
          "emergency_contact_name": null,
          "emergency_contact_phone": null
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
Origin: http://bernhard-rodriguez.mgrapp.com
Authorization: Bearer ad37cb58-6dfd-4315-bce9-5d88019e7f1a
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
Access-Control-Allow-Origin: http://bernhard-rodriguez.mgrapp.com
Access-Control-Allow-Methods: GET,PUT,POST,DELETE
Access-Control-Allow-Headers: Authorization,Content-Type
Vary: Origin
ETag: W/&quot;5bf38f34531d2c865be26956165ac621&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 35d88ce2-0b4a-447b-850c-c4801877972b
X-Runtime: 0.115502
Content-Length: 2604
200 OK
```


```json
{
  "transactions": [
    {
      "id": "ef02036b-9863-4b2c-b76b-cb33cb5d8891",
      "created_at": "2019-03-13T18:33:00.785Z",
      "state": "pending_capture",
      "amount": "60.0",
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
      "id": "32aea3dc-bff0-41ce-97d9-c80467e08007",
      "created_at": "2019-03-13T18:33:00.783Z",
      "state": "pending_capture",
      "amount": "12.0",
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
      "id": "3dadc069-a110-417a-be05-8665a14894e2",
      "created_at": "2019-03-13T18:33:00.781Z",
      "state": "pending_capture",
      "amount": "7.0",
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
      "id": "9657ab09-6ef0-4db4-828e-19b50dc52c99",
      "created_at": "2019-03-13T18:33:00.779Z",
      "state": "pending_capture",
      "amount": "58.0",
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
      "id": "f8da4c94-2760-4e7d-8aa3-a37ef846e656",
      "created_at": "2019-03-13T18:33:00.775Z",
      "state": "pending_capture",
      "amount": "50.0",
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



