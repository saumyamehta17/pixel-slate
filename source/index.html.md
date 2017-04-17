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

# User

##  With Referral Code / Update User with address
> Request Format

```json
  {
       "name": "SM", 
       "email": "ss",
       "referral_code": "1E0XGE",
       "address": {"pincode": "122001", 
             "state": "HRY", 
             "house": 230, 
             "locality": "Park View",
             "name": "GGN", 
             "number": "11111111"}
      }
```

### HTTP REQUEST
`PUT /api/v1/users/:id`