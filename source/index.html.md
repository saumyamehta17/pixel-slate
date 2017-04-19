---
title: API Reference

<!-- language_tabs:
  - shell
  - ruby
  - python
  - javascript -->

<!-- toc_footers: -->
  <!-- - <a href='#'>Sign Up for a Developer Key</a> -->
  <!-- - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a> -->

includes:
  - errors

search: true
---

# Config Api

## get all config var

### HTTP REQUEST
`GET /api/v1/rate_card` // HEADERS - LANG, COUNTRY_CODE 

# User

## Generate OTP for new User
> Request Format

```json
  {
    "number": "9090909090"
  }
```

### HTTP REQUEST
`POST /api/v1/otp/generate_otp`

## Verify new User with OTP
> Request Format

```json
  {
    "number": "9090909090", 
    "code": "1111"
  }
```

### HTTP REQUEST
`POST /api/v1/otp/verify`

##  Update User with address and other details
> Request Format

```json
  {
   "name": "SM", 
   "email": "sm@pixel.com",
   "dob": "17-12-1989",
   "referral_code": "1E0XGE",
   "address": 
        {
         "pincode": "122001", 
         "state": "HRY", 
         "house": 230, 
         "locality": "Park View",
         "name": "GGN", 
         "number": "11111111"
        }
  }
```

### HTTP REQUEST
`PUT /api/v1/users/:id`

##  Only Referral
> Request Format

```json
  {
    "referral_code": "1E0XGE"
  }
```

## Get successful referrals

### HTTP REQUEST
`GET api/v1/users/referral_used`

## GET user profile

> Request Format

```json
 NOT REQUIRED
```
### HTTP REQUEST
`GET /api/v1/users/:id`

# Address

## Create an address

```json
 {
   "address": {
               "house": 230, "locality": "Park View","pincode": 122001, "state": "HRY", 
               "landmark": "Near Castle GRDN", "name": 'GGN', number: '9090909090'
              }
 }
```
### HTTP REQUEST
`POST /api/v1/addresses`

## update an address

```json
 {
   "address": {
               "house": 230, "locality": "Park View","pincode": 122001, "state": "HRY", 
               "landmark": "Near Castle GRDN", "name": 'GGN', number: '9090909090'
              }
 }
```
### HTTP REQUEST
`PUT /api/v1/addresses/:id`

## delete an address

### HTTP REQUEST
`DELETE api/v1/addresses/:id`

# Coupons

## Get list of coupons which is applicable to user

> Request Format

```json
 Not required
```

### HTTP REQUEST
`GET /api/v1/coupons?amount=1200&&referral=true`  //amount/referral is optional, where referral param tells to get all coupons as a reward of referral

## Verify a coupon on app, shows message accordingly
> Request Format

```json
  {
    "coupon":
    {
      "promo_code": "DIW20"
    }
  }
```
### HTTP REQUEST
`POST api/v1/coupons/verify?amount=500`  //amount is optional

# Orders

## get all orders
```json
 NOT REQUIRED
```

### HTTP REQUEST
`GET /api/v1/orders/`

## Create an order
```json
  {
    "order": {
      "items":
      [{
        "size": "3 x 5",  as meteres
        "type": "Glossy", as second
        "print": 2,
        "uuid": "123334433sddd"
      },{
        .... similar to above .....
      }],
      address_id: '58a57aaa2980d33040286a54'
    } 
  }
```

### HTTP REQUEST
`POST /api/v1/orders`

## regenerate upload path
```json
 {
  "order_id": "589aaad68f92d20a4433ea78",
  "uuids": ["123334433sddd", ""]
 }
```

### HTTP REQUEST
`POST /api/v1/orders/regenerate_path`

## tax calculate

### HTTP REQUEST
`GET /api/v1/orders/tax_calculate`

## dummy_urls

### HTTP REQUEST
`GET api/v1/orders/dummy_urls?order_id`

# Order V2

## Order get details

> Request

```json
# POST /api/v1/orders/get_details
  {
    "order": {
      "items":
    [{
    "key": "photo/small/4x6",
    "print": 2,
    "uuid": ["123334433sddd", "dsd433sddd", "433sddds88999"]
  },{
  .... similar to above .....
  }],
  address_id: '58a57aaa2980d33040286a54'
  } }
---
```

> Response

```json
{
  "success": 1,
  "order": {
    "_id": "58f6ff682980d3150cf5dbd8",
    "address_id": "58f48c922980d36073e483cf",
    "base_amount": 320,
    "c_at": null,
    "delivery_date": "2017-04-21T06:10:48.365+00:00",
    "gateway": "payu",
    "net_amount": 368,
    "sessions": [
      {
        "_id": "58f6ff682980d3150cf5dbda",
        "amount": 60,
        "key": "photo/small/4x6",
        "print": 2,
        "uuid": [
          "123334433sddd",
          "dsd433sddd",
          "433sddds88999"
        ]
      },
      {
        "_id": "58f6ff682980d3150cf5dbdc",
        "amount": 50,
        "key": "photo/small/3.5x5",
        "print": 2,
        "uuid": [
          "123334433sdd2",
          "dsd413sddd",
          "233sddds88999"
        ]
      }
    ],
    "shipping_charge": 100,
    "status": "order_open",
    "t_hash": null,
    "tax": {
      "_id": "58f6ff682980d3150cf5dbdd",
      "c_at": null,
      "service_tax": 48,
      "total": 48,
      "vat": 0
    },
    "taxable_amount": 320,
    "txn_id": "1T1EB-FXE3F-TC8R0",
    "user_id": "58f4b53d2980d30500523488"
  }
}
```

### HTTP REQUEST
`POST /api/v1/orders/get_details`