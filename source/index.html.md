---
title: MGR API Documentation
language_tabs:
  - json: JSON
  - shell: cURL
---

TODO some description of the API here
# Business Accounts

A Business Account is a gym or studio with one or many locations.
It is the top-level entity for pretty much everything.
By accessing the API from a specific domain, you are generally mapping to a specific business account.


## Get Current

Ask the API for what my current Business Account is based on host origin.

### Request

#### Endpoint

```plaintext
GET /api/business_accounts/current
Origin: http://quigley.biz
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
ETag: W/&quot;9df4237db89233d974cdc645305f7117&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: af5f3d08-f692-41b3-b42e-00ba2c1400f8
X-Runtime: 0.010824
Content-Length: 1444
200 OK
```


```json
{
  "business_account": {
    "id": "711da8dd-6bcb-4e14-b13b-817461c74185",
    "name": "Cummerata, Kiehn and Wiegand",
    "slug": "cummerata-kiehn-and-wiegand",
    "business_type": "fitness_studio",
    "account_type": null,
    "requires_waiver": true,
    "waiver_text": null,
    "waiver_url": null,
    "locations": [
      {
        "id": "aae5fcb9-d310-4736-bca2-fd50e0c071af",
        "name": "Fahey, Stracke and Ziemann",
        "slug": "fahey-stracke-and-ziemann",
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
        "id": "a6e19384-1d9a-468c-b920-02d3ba4f0846",
        "name": "Wehner, Quigley and Eichmann",
        "slug": "wehner-quigley-and-eichmann",
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
        "id": "3437491d-146a-4f15-99f9-06104e8f6616",
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
        "id": "58f5852a-cd0f-42d1-bef4-757f7e9652a3",
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
Origin: http://spencer-marks.mgrapp.com
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
ETag: W/&quot;ebb895abdcca6341bc3e9ae3360287bf&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d6b82602-29db-4313-a229-1b7e9040168f
X-Runtime: 0.016595
Content-Length: 1441
200 OK
```


```json
{
  "business_staffs": [
    {
      "id": "8e574aba-d012-41bd-9175-be550986ad87",
      "email": "heike_ondricka@kovacek.ca",
      "slug": "rebekah-bernier",
      "first_name": "Rebekah",
      "last_name": "Bernier",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": {
        "id": null,
        "file_type": "image/png",
        "key": "default",
        "width": 300,
        "height": 300,
        "file_size": null,
        "orig_filename": "300.png",
        "is_image": true,
        "url": "http://placehold.it/300/300"
      },
      "roles": [
        {
          "id": "36d6698b-2786-499d-9747-2bd9caa3808e",
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
      "id": "21cd8fae-1735-4a94-9173-338a494fd8a8",
      "email": "sterling_auer@bode.biz",
      "slug": "joyce-pacocha",
      "first_name": "Joyce",
      "last_name": "Pacocha",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": {
        "id": null,
        "file_type": "image/png",
        "key": "default",
        "width": 300,
        "height": 300,
        "file_size": null,
        "orig_filename": "300.png",
        "is_image": true,
        "url": "http://placehold.it/300/300"
      },
      "roles": [
        {
          "id": "36d6698b-2786-499d-9747-2bd9caa3808e",
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
Origin: http://macejkovic-breitenberg.mgrapp.com
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
ETag: W/&quot;1175a359a36fe928734eab57189befdb&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: a06fbb37-d4fb-454f-a506-825b1fc27aba
X-Runtime: 0.034653
Content-Length: 2343
200 OK
```


```json
{
  "business_staffs": [
    {
      "id": "20afdd67-abe1-4413-a3f7-eda17ba9962b",
      "email": "charlesetta@pacocharyan.name",
      "slug": "kristan-shanahan",
      "first_name": "Kristan",
      "last_name": "Shanahan",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": {
        "id": null,
        "file_type": "image/png",
        "key": "default",
        "width": 300,
        "height": 300,
        "file_size": null,
        "orig_filename": "300.png",
        "is_image": true,
        "url": "http://placehold.it/300/300"
      },
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
      "id": "b86bc665-0d2f-4124-84f6-b748a5deae00",
      "email": "callie@feil.info",
      "slug": "monique-roberts",
      "first_name": "Monique",
      "last_name": "Roberts",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": {
        "id": null,
        "file_type": "image/png",
        "key": "default",
        "width": 300,
        "height": 300,
        "file_size": null,
        "orig_filename": "300.png",
        "is_image": true,
        "url": "http://placehold.it/300/300"
      },
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
      "id": "20f653e7-7bfd-47c0-b37b-2507eb7f98d9",
      "email": "charlie@runte.com",
      "slug": "sharyl-hermiston",
      "first_name": "Sharyl",
      "last_name": "Hermiston",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": {
        "id": null,
        "file_type": "image/png",
        "key": "default",
        "width": 300,
        "height": 300,
        "file_size": null,
        "orig_filename": "300.png",
        "is_image": true,
        "url": "http://placehold.it/300/300"
      },
      "roles": [
        {
          "id": "021c9074-d765-4562-ae38-948f15f2a9d5",
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
      "id": "360d5d5a-36b0-42c0-b659-606bd9d78bc6",
      "email": "jay@spencer.us",
      "slug": "catalina-bernhard",
      "first_name": "Catalina",
      "last_name": "Bernhard",
      "description": null,
      "hire_date": null,
      "phone": null,
      "profile_image": {
        "id": null,
        "file_type": "image/png",
        "key": "default",
        "width": 300,
        "height": 300,
        "file_size": null,
        "orig_filename": "300.png",
        "is_image": true,
        "url": "http://placehold.it/300/300"
      },
      "roles": [
        {
          "id": "021c9074-d765-4562-ae38-948f15f2a9d5",
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
Origin: http://ullrich-bogan-and-huels.mgrapp.com
Authorization: Bearer e038854d-957f-4664-9d7c-bf5c3e5cb225
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/gift_cards/redeem`

#### Parameters


```json
code=0E668FC3
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
ETag: W/&quot;de530e40205dc62b731dd76aee1f52e8&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 35a9c236-4b83-4015-b2a7-5203e14ce459
X-Runtime: 0.037888
Content-Length: 1181
201 Created
```


```json
{
  "gift_card_instance": {
    "id": "d66c2f22-bd89-4195-8828-3505bf50e983",
    "gift_card_type": "cash",
    "amount": "11.0",
    "code": "0E668FC3",
    "num_sessions": 0,
    "created_at": "2018-12-18T01:09:31.008Z",
    "redeemed_at": "2018-12-18T01:09:31.028Z",
    "redeemer": {
      "email": "renata@jastklocko.name"
    }
  },
  "transaction": {
    "id": "f9b532b9-8c70-4daf-82d4-21aaa243cb23",
    "created_at": "2018-12-18T01:09:31.035Z",
    "state": "complete",
    "amount": "-11.0",
    "fail_message": null,
    "process_after": null,
    "processed_at": "2018-12-18T01:09:31.045Z",
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
      "balance": "111.0",
      "is_default": null
    },
    "transactable": null,
    "creator_type": null,
    "creator": null
  },
  "package_instance": null,
  "user_profile": {
    "id": "e4e23a25-f770-4548-ba37-da17c0c63e16",
    "account_balance": "111.0",
    "signed_waiver_at": null,
    "created_at": "2018-12-18T01:09:31.016Z",
    "email": "renata@jastklocko.name",
    "first_name": "Arielle",
    "last_name": "Collier",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2018-12-17"
  }
}
```



# Offerings

Specific instances of a class that a user can sign up for

## Filter By Location


### Request

#### Endpoint

```plaintext
GET /api/offerings?time_zone_offset=420&amp;location_id=0b27d0dd-c148-412e-94db-ced8b949f576
Origin: http://swaniawski-powlowski-and-larson.mgrapp.com
Host: example.org
Cookie: 
```

`GET /api/offerings`

#### Parameters


```json
time_zone_offset: 420
location_id: 0b27d0dd-c148-412e-94db-ced8b949f576
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
ETag: W/&quot;671cd345522d859993fd60ade140f43d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: d10b074a-8ba6-4595-88cc-46ab7b1a9127
X-Runtime: 0.017387
Content-Length: 4866
200 OK
```


```json
{
  "offerings": [
    {
      "id": "f9404e5f-6734-4e63-bdac-af89b70e7cb5",
      "name": "Milky Affineurs 8afb6078",
      "resource_slug": "milky-affineurs-8afb6078",
      "description": "Blue fungi in cream cut the cheese bergkäse from the Alps they can also age quite well in ripening cellars where bergkäse from the Alps of cheesy business lingo cut to size so cute but cheesy the sticky nature of processed cheese can make it difficult to slice, but they can also age quite well in ripening cellars where.",
      "resource_type": null,
      "start_time": "2018-08-21T09:00:00.000Z",
      "end_time": "2018-08-21T10:00:00.000Z",
      "reservation_cutoff_time": "2018-08-21T09:00:00.000Z",
      "waitlist_cutoff_time": "2018-08-21T09:00:00.000Z",
      "late_cancel_cutoff_time": "2018-08-21T09:00:00.000Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Carter-Hartmann",
      "location_id": "0b27d0dd-c148-412e-94db-ced8b949f576",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "3269b796-f373-4539-a59b-531df39969cc",
        "email": "zachariah.larkin@beckerlebsack.ca",
        "slug": "star-jacobi",
        "first_name": "Star",
        "last_name": "Jacobi",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "d365539e-3f74-4539-a857-42bd6ed185d5",
      "name": "Nutty Coulommiers ddb0c546",
      "resource_slug": "nutty-coulommiers-ddb0c546",
      "description": "What do you call cheese that isn't yours? nacho cheese; they can also age quite well in ripening cellars where is like chalk and cheese the slice of cheese is placed on top of the meat patty but poets have been mysteriously silent on the subject of cheese bergkäse from the Alps cheeseparing New York cheesecake taste and texture in all colours Penicillium roqueforti.",
      "resource_type": null,
      "start_time": "2018-08-22T05:00:00.000Z",
      "end_time": "2018-08-22T06:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T05:00:00.000Z",
      "waitlist_cutoff_time": "2018-08-22T05:00:00.000Z",
      "late_cancel_cutoff_time": "2018-08-22T05:00:00.000Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Carter-Hartmann",
      "location_id": "0b27d0dd-c148-412e-94db-ced8b949f576",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "4c4e04f6-4249-41b3-8ff4-f09080c7043a",
        "email": "jacquelin@mclaughlin.biz",
        "slug": "alesia-hettinger",
        "first_name": "Alesia",
        "last_name": "Hettinger",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "1f6f899c-77a0-4824-aac9-857ca2aee9f7",
      "name": "Milky Affineurs 8afb6078",
      "resource_slug": "milky-affineurs-8afb6078",
      "description": "Blue fungi in cream cut the cheese bergkäse from the Alps they can also age quite well in ripening cellars where bergkäse from the Alps of cheesy business lingo cut to size so cute but cheesy the sticky nature of processed cheese can make it difficult to slice, but they can also age quite well in ripening cellars where.",
      "resource_type": null,
      "start_time": "2018-08-22T17:00:00.000Z",
      "end_time": "2018-08-22T18:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T17:00:00.000Z",
      "waitlist_cutoff_time": "2018-08-22T17:00:00.000Z",
      "late_cancel_cutoff_time": "2018-08-22T17:00:00.000Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Carter-Hartmann",
      "location_id": "0b27d0dd-c148-412e-94db-ced8b949f576",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "346af457-ff22-4739-8742-1a9225aa551b",
        "email": "zenia_weber@dooleythompson.us",
        "slug": "clarine-ritchie",
        "first_name": "Clarine",
        "last_name": "Ritchie",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
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
Origin: http://hirthe-satterfield-and-o-conner.mgrapp.com
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
ETag: W/&quot;2ca026cbd1592c5896c99775bb2d8e6d&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0731d673-db2d-4ae4-9886-b13a0d61b2e5
X-Runtime: 0.023967
Content-Length: 4949
200 OK
```


```json
{
  "offerings": [
    {
      "id": "27ba4310-bf47-4987-b6a2-5e3d20b973fc",
      "name": "Cheeky Coulommiers 6d24e89f",
      "resource_slug": "cheeky-coulommiers-6d24e89f",
      "description": "The sticky nature of processed cheese can make it difficult to slice, but cheese paring with wine garlic cheese biscuits Penicillium roqueforti coagulation of the milk protein casein they were so cheesed off is like chalk and cheese he old cheese dairy buildings, situated on the historic site is like chalk and cheese washed curd cheese.",
      "resource_type": null,
      "start_time": "2018-08-21T09:00:00.000Z",
      "end_time": "2018-08-21T10:00:00.000Z",
      "reservation_cutoff_time": "2018-08-21T09:00:00.000Z",
      "waitlist_cutoff_time": "2018-08-21T09:00:00.000Z",
      "late_cancel_cutoff_time": "2018-08-21T09:00:00.000Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Hoppe, Orn and Howe",
      "location_id": "e4f30b3a-bf53-4640-ae39-5c6e677fe978",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "bd8eed3a-c52e-482c-8ba5-17c67b6a356e",
        "email": "lindsay.murazik@bernierpowlowski.name",
        "slug": "fernando-hettinger",
        "first_name": "Fernando",
        "last_name": "Hettinger",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "40866d6d-445c-4063-bf53-c9b991d34429",
      "name": "Dutch Gouda 291b52c0",
      "resource_slug": "dutch-gouda-291b52c0",
      "description": "Blessed are the cheesemakers the early bird may get the worm, but the second mouse gets the cheese in the trap is like chalk and cheese he old cheese dairy buildings, situated on the historic site is like chalk and cheese it is blue sky thinking the sticky nature of processed cheese can make it difficult to slice, but of the Friesian herd cut the cheese but don't you agree? It is no use crying over spilled milk.",
      "resource_type": null,
      "start_time": "2018-08-22T05:00:00.000Z",
      "end_time": "2018-08-22T06:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T05:00:00.000Z",
      "waitlist_cutoff_time": "2018-08-22T05:00:00.000Z",
      "late_cancel_cutoff_time": "2018-08-22T05:00:00.000Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Hoppe, Orn and Howe",
      "location_id": "e4f30b3a-bf53-4640-ae39-5c6e677fe978",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "d6cbff71-0a2c-4846-a26b-1260a730c80b",
        "email": "ria@oberbrunner.biz",
        "slug": "michelle-ratke",
        "first_name": "Michelle",
        "last_name": "Ratke",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
      },
      "substitute": null,
      "recurrence": null
    },
    {
      "id": "3668d7cc-b683-40a9-b0b8-916824062f82",
      "name": "Cheeky Coulommiers 6d24e89f",
      "resource_slug": "cheeky-coulommiers-6d24e89f",
      "description": "The sticky nature of processed cheese can make it difficult to slice, but cheese paring with wine garlic cheese biscuits Penicillium roqueforti coagulation of the milk protein casein they were so cheesed off is like chalk and cheese he old cheese dairy buildings, situated on the historic site is like chalk and cheese washed curd cheese.",
      "resource_type": null,
      "start_time": "2018-08-22T17:00:00.000Z",
      "end_time": "2018-08-22T18:00:00.000Z",
      "reservation_cutoff_time": "2018-08-22T17:00:00.000Z",
      "waitlist_cutoff_time": "2018-08-22T17:00:00.000Z",
      "late_cancel_cutoff_time": "2018-08-22T17:00:00.000Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 1,
      "num_total_reservations": 0,
      "time_zone": "America/Los_Angeles",
      "location_name": "Hoppe, Orn and Howe",
      "location_id": "e4f30b3a-bf53-4640-ae39-5c6e677fe978",
      "open_for_registration": false,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "59a4a0ac-fdfb-4e1e-8cd4-88e1df64b3b0",
        "email": "inge@buckridge.info",
        "slug": "patience-conn",
        "first_name": "Patience",
        "last_name": "Conn",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
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
Origin: http://cole-frami-and-hessel.mgrapp.com
Authorization: Bearer 23041329-f935-4927-b746-84e83ee47664
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/orders`

#### Parameters


```json
line_items[][variant_id]=55032cda-4fb5-45fe-8bac-b33076fcb26c&line_items[][quantity]=1&payments[][payment_type]=stripe_cc&payments[][source_id]=test_cc_2
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
ETag: W/&quot;caefb2a77a5975112662ff46773e2f3a&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 42939ae7-5726-4000-b491-0933577a101b
X-Runtime: 0.101948
Content-Length: 1578
201 Created
```


```json
{
  "order": {
    "id": "03467edf-5d80-4db7-b20a-faf6085024e4",
    "number": "03467edf",
    "line_items": [
      {
        "id": "f32697c9-0edf-430a-a083-6befa8525de2",
        "quantity": 1,
        "per_unit_price": "67.0",
        "name": "Panacell Digital Side Receiver",
        "variant": {
          "id": "55032cda-4fb5-45fe-8bac-b33076fcb26c",
          "price": "67.0",
          "is_master": true
        }
      }
    ],
    "created_at": "2018-12-18T01:09:31.146Z",
    "total": "0.0",
    "item_total": "67.0",
    "adjustment_total": "0.0",
    "payment_total": "67.0",
    "payment_state": "complete",
    "fulfillment_state": "complete",
    "user": {
      "id": "4118fb76-bd83-42a2-8e61-916651dcc075",
      "account_balance": "0.0",
      "signed_waiver_at": null,
      "created_at": "2018-12-18T01:09:31.077Z",
      "email": "walter.leffler@jenkins.biz",
      "first_name": "Diedre",
      "last_name": "Sawayn",
      "address1": null,
      "address2": null,
      "city": null,
      "state": null,
      "zip_code": null,
      "phone": null,
      "dob": null,
      "member_start_date": "2018-12-17"
    },
    "payments": [
      {
        "id": "5b787c28-51f5-450c-867c-dc863d8bf940",
        "created_at": "2018-12-18T01:09:31.150Z",
        "state": "complete",
        "amount": "67.0",
        "fail_message": null,
        "process_after": null,
        "processed_at": "2018-12-18T01:09:31.172Z",
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
          "id": "03467edf-5d80-4db7-b20a-faf6085024e4",
          "number": "03467edf",
          "total": "0.0",
          "item_total": "67.0",
          "adjustment_total": "0.0",
          "payment_total": "67.0",
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
Origin: http://wehner-jewess.mgrapp.com
Authorization: Bearer 6a03e676-24d4-4ec1-acb5-de73183e592b
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
X-Request-Id: 534a56c2-8c6b-471f-bfee-2aa440b51d65
X-Runtime: 0.019520
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
Origin: http://little-frami-and-borer.mgrapp.com
Authorization: Bearer 614b3617-b5c8-479d-8588-4eed6c7a2be9
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
X-Request-Id: e3a343d7-7fed-48ab-8cc9-3c10c6966f1c
X-Runtime: 0.007944
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
Origin: http://marvin-kessler.mgrapp.com
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
ETag: W/&quot;c77630ca359e17642216a73e84a05732&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 6c2d987c-d2b0-4908-a9b6-ac3620271bba
X-Runtime: 0.015902
Content-Length: 2077
200 OK
```


```json
{
  "products": [
    {
      "id": "68815d87-6968-4b9b-b5ad-1f6898f595b1",
      "name": "Sinepod Input Digital Bridge",
      "slug": "sinepod-input-digital-bridge",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "d1a7069f-cd83-4058-a5c7-b8d840da9fd8",
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
          "id": "7d4f6aea-c7c4-45e5-bdad-38de312a1d19",
          "price": "76.0",
          "is_master": true
        }
      ],
      "price": "76.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
    },
    {
      "id": "f27b546b-569b-454f-ac80-45e7a3c7920c",
      "name": "Tryffe Tag Kit",
      "slug": "tryffe-tag-kit",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "d63220e4-d494-43a5-bdcd-db1ef41bf8b7",
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
          "id": "d781e9c3-1425-4508-9855-4f580ce022d2",
          "price": "52.0",
          "is_master": true
        }
      ],
      "price": "52.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
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
Origin: http://hahn-ernser-and-wiegand.mgrapp.com
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
ETag: W/&quot;0926b98971e6d69ee33415dd1003d9ee&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 5c0d9377-b0aa-4703-816b-2831d2f4e895
X-Runtime: 0.030898
Content-Length: 3887
200 OK
```


```json
{
  "products": [
    {
      "id": "2348047e-8113-4dc2-8668-8a2dc286cf6f",
      "name": "Techfunc Video Transmitter",
      "slug": "techfunc-video-transmitter",
      "description": null,
      "product_type": "normal",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": null,
      "variants": [
        {
          "id": "043d5b2a-e4e2-4d75-a7d4-af06dfc82fe9",
          "price": "31.0",
          "is_master": true
        }
      ],
      "price": "31.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
    },
    {
      "id": "7b565306-07c3-463d-9bce-fedd7b79ec34",
      "name": "Lusync Power Filter",
      "slug": "lusync-power-filter",
      "description": null,
      "product_type": "normal",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": null,
      "variants": [
        {
          "id": "bba1f7e3-d779-4ce9-b576-1e587f570fc5",
          "price": "65.0",
          "is_master": true
        }
      ],
      "price": "65.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
    },
    {
      "id": "b4ed0e81-86af-4a60-8bea-2cafd04f6e44",
      "name": "Trancewood Direct Air Tuner",
      "slug": "trancewood-direct-air-tuner",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "3a8e1061-c0ed-4fd6-a749-51ece48d89f8",
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
          "id": "da199876-4a94-47f2-b3f6-9e9d0347f35d",
          "price": "14.0",
          "is_master": true
        }
      ],
      "price": "14.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
    },
    {
      "id": "46265cb9-363d-42b0-ae4b-8763620fe097",
      "name": "Phentwood Side Input Component",
      "slug": "phentwood-side-input-component",
      "description": null,
      "product_type": "package",
      "available": true,
      "available_online": true,
      "package": {
        "id": "dabcdbdd-effe-45e1-99c1-0578e9ab8d6a",
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
          "id": "1a3237df-d4c2-4155-bc4d-0ea57ad667c0",
          "price": "91.0",
          "is_master": true
        }
      ],
      "price": "91.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
    },
    {
      "id": "32fcc74b-fadf-4acc-83a8-311f3040307a",
      "name": "Techsche Digital Adapter",
      "slug": "techsche-digital-adapter",
      "description": null,
      "product_type": "gift_card",
      "available": true,
      "available_online": true,
      "package": null,
      "gift_card": {
        "id": "15bde23e-7be8-40b6-8636-84bad6e17abe",
        "gift_card_type": "cash",
        "fixed_amount": true,
        "amount": "20.0",
        "num_sessions": 0
      },
      "variants": [
        {
          "id": "d1bc6e9a-8437-4de3-bdc5-a4e97be02d14",
          "price": "13.0",
          "is_master": true
        }
      ],
      "price": "13.0",
      "image": {
        "id": null,
        "file_type": "image/png",
        "key": "product",
        "width": 480,
        "height": 480,
        "file_size": 33800,
        "orig_filename": "product.png",
        "is_image": true,
        "url": "https://mgrapp.s3.amazonaws.com/test/default/assets/1/product"
      }
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
Origin: http://schowalter-becker.mgrapp.com
Authorization: Bearer 44167f36-abd4-4b94-9211-b2341f659312
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/reservations`

#### Parameters


```json
resource_offering_id=80580eb9-7843-4545-94ee-110739c08663&package_instance_id=15739656-bd57-4cda-8f9e-781be2860177
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
ETag: W/&quot;d42dd0321a11cebb3e10126b3ecf8a93&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: c1ee6e2f-5844-4641-8cd4-9c00fdf9f6c3
X-Runtime: 0.052801
Content-Length: 3441
201 Created
```


```json
{
  "reservations": [
    {
      "id": "04193693-a3f5-4b12-9f62-440a78d8d620",
      "state": "reserved",
      "created_at": "2018-12-18T01:09:30.759Z",
      "offering_id": "80580eb9-7843-4545-94ee-110739c08663",
      "package_instance_id": "15739656-bd57-4cda-8f9e-781be2860177",
      "user": {
        "id": "1d660d77-14ba-4dca-8fe9-ce146c68c1c4",
        "first_name": "Clarissa",
        "last_name": "VonRueden",
        "email": "neomi@mills.co.uk"
      },
      "is_guest": false,
      "guest_email": null,
      "guest_name": null,
      "guest_phone": null,
      "note": null,
      "time_zone": "America/Los_Angeles",
      "start_time": "2018-12-18T02:09:30.717Z",
      "signed_in_at": null,
      "resource_name": "Sharp Gouda ddddfa0e",
      "package_name": "Piont Tag Transmitter",
      "location_name": "Pagac-Kautzer",
      "package_expiration_date": null,
      "late_cancel_cutoff_time": "2018-12-18T02:09:30.717Z",
      "waitlist_cutoff_time": "2018-12-18T02:09:30.717Z",
      "end_time": "2018-12-18T03:09:30.717Z",
      "provider": {
        "first_name": "Lisette",
        "last_name": "Kertzmann",
        "description": null,
        "slug": "lisette-kertzmann"
      },
      "substitute": null
    }
  ],
  "offerings": [
    {
      "id": "80580eb9-7843-4545-94ee-110739c08663",
      "name": "Sharp Gouda ddddfa0e",
      "resource_slug": "sharp-gouda-ddddfa0e",
      "description": "Blue fungi in cream trying too hard, unsubtle, and inauthentic and wrap blue cheeses all over as mould spores spread readily the sticky nature of processed cheese can make it difficult to slice, but wash, rinse, repeat What do you call cheese that isn't yours? Nacho Cheese; 10 grilled cheese sandwiches you should try immediately with soft ripening cheese for but poets have been mysteriously silent on the subject of cheese harmful secondary metabolites.",
      "resource_type": null,
      "start_time": "2018-12-18T02:09:30.717Z",
      "end_time": "2018-12-18T03:09:30.717Z",
      "reservation_cutoff_time": "2018-12-18T02:09:30.717Z",
      "waitlist_cutoff_time": "2018-12-18T02:09:30.717Z",
      "late_cancel_cutoff_time": "2018-12-18T02:09:30.717Z",
      "late_cancel_grace_period_in_minutes": 0,
      "waitlist_allowed": true,
      "waitlist_capacity": 0,
      "num_waitlist_reservations": 0,
      "normal_capacity": 10,
      "num_total_reservations": 1,
      "time_zone": "America/Los_Angeles",
      "location_name": "Pagac-Kautzer",
      "location_id": "f26f922b-b795-4a82-bfd7-aebe0797e30e",
      "open_for_registration": true,
      "pre_reservation_message": null,
      "post_reservation_message": null,
      "substitute_request": null,
      "provider": {
        "id": "274570b7-1ee3-420f-bf61-8b2ac1aa0cf3",
        "email": "crissy@donnellylegros.us",
        "slug": "lisette-kertzmann",
        "first_name": "Lisette",
        "last_name": "Kertzmann",
        "description": null,
        "hire_date": null,
        "phone": null,
        "profile_image": {
          "id": null,
          "file_type": "image/png",
          "key": "default",
          "width": 300,
          "height": 300,
          "file_size": null,
          "orig_filename": "300.png",
          "is_image": true,
          "url": "http://placehold.it/300/300"
        }
      },
      "substitute": null,
      "recurrence": null
    }
  ],
  "packages": [
    {
      "id": "15739656-bd57-4cda-8f9e-781be2860177",
      "name": "Piont Tag Transmitter",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 10,
      "sessions_remaining": 10,
      "created_at": "2018-12-18T01:09:30.689Z",
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
          "id": "1d660d77-14ba-4dca-8fe9-ce146c68c1c4",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-18T01:09:30.698Z",
          "email": "neomi@mills.co.uk",
          "first_name": "Clarissa",
          "last_name": "VonRueden",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-17"
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
Origin: http://mcglynn-kirlin.mgrapp.com
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
ETag: W/&quot;9a97c6e8948711106a13ff846b2aae08&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 4c6b405b-7a1d-4122-962c-77e95e666aad
X-Runtime: 0.096569
Content-Length: 1621
200 OK
```


```json
{
  "resources": [
    {
      "id": "c8f99169-3029-4504-a5b9-bda4ae454a3b",
      "name": "Sharp Goats 2bd39a3a",
      "slug": "sharp-goats-2bd39a3a",
      "description": "Taste and texture in all colours 10 grilled cheese sandwiches you should try immediately with in an artisan farmerhouse the slice of cheese is placed on top of the meat patty raw milk is unpasteurized applewood smoked dutch sandwich team cheesy says hi Sheridans Cheesemongers the early bird may get the worm, but the second mouse gets the cheese in the trap.",
      "resource_type": null,
      "comments": [

      ]
    },
    {
      "id": "80399458-66d4-4b88-a4c8-330dece6305d",
      "name": "Soft Alpine a5871976",
      "slug": "soft-alpine-a5871976",
      "description": "Cut to size is like chalk and cheese cheese paring with wine until the wheels form a white coat of penicillium moulds dutch sandwich - tongue in cheek garlic cheese biscuits the sticky nature of processed cheese can make it difficult to slice, but wash, rinse, repeat and wrap blue cheeses all over as mould spores spread readily.",
      "resource_type": null,
      "comments": [

      ]
    },
    {
      "id": "3fe0884c-bc3f-45ef-94ba-e6d27d863fed",
      "name": "Melting Dairy fe34551e",
      "slug": "melting-dairy-fe34551e",
      "description": "Blue fungi in cream the milky way of the sticky nature of processed cheese can make it difficult to slice, but separate the curds from the wey the milky way of processed cheese has several technical advantages over traditional cheese of the Friesian herd it is blue sky thinking with Dutch courage salt, pepper, mustard and vinegar.",
      "resource_type": null,
      "comments": [

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



# User Account

User profile and account information

## Get Session


### Request

#### Endpoint

```plaintext
GET /api/users/me
Origin: http://leannon-dicki.mgrapp.com
Authorization: Bearer 72d9c550-6062-4382-aae8-46e54b1544b4
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
ETag: W/&quot;ae065fdd633b4f35aefeab17d8514f9b&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 98492531-f011-4578-952f-993628aab084
X-Runtime: 0.023303
Content-Length: 443
200 OK
```


```json
{
  "session": {
    "id": "72d9c550-6062-4382-aae8-46e54b1544b4",
    "expires_at": "2019-01-01T01:09:30.102Z"
  },
  "user": {
    "id": "0ff4757a-53ce-4f57-88d8-b8dad880fdf9",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2018-12-18T01:09:30.100Z",
    "email": "ciara.kiehn@hoppe.info",
    "first_name": "Allene",
    "last_name": "Tromp",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2018-12-17"
  }
}
```



## Register


### Request

#### Endpoint

```plaintext
POST /api/users
Origin: http://jewess-jaskolski.mgrapp.com
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
ETag: W/&quot;d972207ea1690a70229a2ea6c3a8bab9&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0298c61b-4d08-4919-b927-9d58bb3eb9be
X-Runtime: 0.015164
Content-Length: 458
201 Created
```


```json
{
  "session": {
    "id": "3965d616-9bd9-424b-9ec3-1b9bbf9d7fbe",
    "expires_at": null
  },
  "user": {
    "id": "3c119e27-cf1b-4712-972b-9d4bfe902a59",
    "account_balance": "0.0",
    "signed_waiver_at": "2018-12-18T01:09:30.182Z",
    "created_at": "2018-12-18T01:09:30.184Z",
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
    "member_start_date": "2018-12-17"
  }
}
```



## Sign In


### Request

#### Endpoint

```plaintext
POST /api/users/session
Origin: http://vandervort-pagac.mgrapp.com
Host: example.org
Content-Type: application/x-www-form-urlencoded
Cookie: 
```

`POST /api/users/session`

#### Parameters


```json
email=hollis_ebert%40gutmannhackett.biz&password=password
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
ETag: W/&quot;2bb2fa269e4746abe3079f0f0ec90ab5&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 0b1e095e-21b9-41a1-a9cb-1f161a6cd4e1
X-Runtime: 0.011683
Content-Length: 432
201 Created
```


```json
{
  "session": {
    "id": "51044922-ab54-46e5-a001-8c06d6ceca80",
    "expires_at": null
  },
  "user": {
    "id": "63857887-6cc7-4d34-ae01-3b39dff1a575",
    "account_balance": "0.0",
    "signed_waiver_at": null,
    "created_at": "2018-12-18T01:09:30.143Z",
    "email": "hollis_ebert@gutmannhackett.biz",
    "first_name": "Archie",
    "last_name": "Dibbert",
    "address1": null,
    "address2": null,
    "city": null,
    "state": null,
    "zip_code": null,
    "phone": null,
    "dob": null,
    "member_start_date": "2018-12-17"
  }
}
```



## Sign Out


### Request

#### Endpoint

```plaintext
DELETE /api/users/session
Origin: http://bogisich-schoen.mgrapp.com
Authorization: Bearer 818c0fde-ac67-4080-bff9-8054f4165099
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
X-Request-Id: 1288f5af-8e3e-4e48-b5bf-e36f5dff6fe7
X-Runtime: 0.008217
204 No Content
```




# User Package

Used by a client to book classes

## Get All


### Request

#### Endpoint

```plaintext
GET /api/user_packages
Origin: http://vonrueden-legros.mgrapp.com
Authorization: Bearer 539fb082-c856-46f1-9bd0-a4b61b8a7700
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
ETag: W/&quot;41c87b731d83cce1e512dd229784616e&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: e5f5951a-b282-4686-9bef-d46219a8105a
X-Runtime: 0.032577
Content-Length: 2440
200 OK
```


```json
{
  "packages": [
    {
      "id": "fa63675b-11a9-4775-8086-ebfc491b1ee1",
      "name": "Phounewood Electric Viewer",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2018-12-18T01:09:30.396Z",
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
          "id": "3f699430-2541-446b-b4c0-1f235e914d0f",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-18T01:09:30.234Z",
          "email": "mac.konopelski@runtebogisich.ca",
          "first_name": "Bunny",
          "last_name": "Harvey",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-17"
        }
      ]
    },
    {
      "id": "5b23e760-2aad-478f-82c7-8307a5282a56",
      "name": "Trackwood Side Compressor",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2018-12-18T01:09:30.387Z",
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
          "id": "3f699430-2541-446b-b4c0-1f235e914d0f",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-18T01:09:30.234Z",
          "email": "mac.konopelski@runtebogisich.ca",
          "first_name": "Bunny",
          "last_name": "Harvey",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-17"
        }
      ]
    },
    {
      "id": "00b7ec54-a7e8-432b-a7a1-e15cb102e867",
      "name": "Traphwood HD Tuner",
      "state": "active",
      "start_date": null,
      "end_date": null,
      "unlimited_sessions": true,
      "total_sessions": 1,
      "sessions_remaining": 1,
      "created_at": "2018-12-18T01:09:30.368Z",
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
          "id": "3f699430-2541-446b-b4c0-1f235e914d0f",
          "account_balance": "0.0",
          "signed_waiver_at": null,
          "created_at": "2018-12-18T01:09:30.234Z",
          "email": "mac.konopelski@runtebogisich.ca",
          "first_name": "Bunny",
          "last_name": "Harvey",
          "address1": null,
          "address2": null,
          "city": null,
          "state": null,
          "zip_code": null,
          "phone": null,
          "dob": null,
          "member_start_date": "2018-12-17"
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
Origin: http://berge-group.mgrapp.com
Authorization: Bearer 241ff5a2-e222-48ae-9e8a-41db1ea6dcfa
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
ETag: W/&quot;c1107a994f425375ccc58e2553cbc8a4&quot;
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: 15731e70-e984-49d8-9e0d-96c502ec7ff6
X-Runtime: 0.013142
Content-Length: 2605
200 OK
```


```json
{
  "transactions": [
    {
      "id": "92db7323-6c29-48f1-90b2-a13181469e55",
      "created_at": "2018-12-18T01:09:30.650Z",
      "state": "pending_capture",
      "amount": "29.0",
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
      "id": "955bfd72-1a78-4620-81ec-0e2b9b85b01b",
      "created_at": "2018-12-18T01:09:30.648Z",
      "state": "pending_capture",
      "amount": "61.0",
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
      "id": "bd1c9068-231e-4b40-a664-9818af44c8da",
      "created_at": "2018-12-18T01:09:30.646Z",
      "state": "pending_capture",
      "amount": "63.0",
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
      "id": "34e2aac4-e7d2-4ffe-9be9-071cbc669f73",
      "created_at": "2018-12-18T01:09:30.644Z",
      "state": "pending_capture",
      "amount": "40.0",
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
      "id": "9b59f563-fdca-4f57-b53f-978538d85882",
      "created_at": "2018-12-18T01:09:30.641Z",
      "state": "pending_capture",
      "amount": "41.0",
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



