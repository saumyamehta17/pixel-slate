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

##  SignUp or register or Update User with address and other details with or without referral_code
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

##  Only Referral after signup
> Request Format

```json
  {
    "referral_code": "1E0XGE"
  }
```

### HTTP REQUEST
`POST api/v1/users/use_referral`

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

## Get list of coupons which is applicable to user or coupons that earned via referrals or get coupons on amount

### HTTP REQUEST
`GET /api/v1/coupons` // Get all applicable for givem user
`GET /api/v1/coupons?amount=1200`  //Get all coupon on given amount 
`GET /api/v1/coupons?referral=true`  //Get all coupon that a user earned from referrals

# Orders

## get all orders
```json
 NOT REQUIRED
```

### HTTP REQUEST
`GET /api/v1/orders/`

## Get details of before creating order
```json
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
      address_id: '58a57aaa2980d33040286a54',
      coupon: "FIRST" // Optional
  } }
```

### HTTP REQUEST
`POST /api/v1/orders/get_details`

## Create an order
```json
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
      "address_id": '58a57aaa2980d33040286a54'.
      "gateway": "payu" or "paytm",
      "coupon": "FIRST" // optional
  } }
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

## dummy_urls

### HTTP REQUEST
`GET api/v1/orders/dummy_urls?order_id`

# Static Content of Home Page

## About Us

### HTTP REQUEST
`GET /api/v1/home_page/about` // NOTE: NO HEADERS EXCEPT If-None-Match

## FAQS

### HTTP REQUEST
`GET /api/v1/home_page/faqs` // NOTE: NO HEADERS EXCEPT If-None-Match

## Privacy Policy

### HTTP REQUEST
`GET /api/v1/home_page/privacy_policy` // NOTE: NO HEADERS EXCEPT If-None-Match

## Terms n Condition

### HTTP REQUEST
`GET /api/v1/home_page/tnc` // NOTE: NO HEADERS EXCEPT If-None-Match
