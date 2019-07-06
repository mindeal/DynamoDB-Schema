# Posts

All kinds of posts(Deals and Articles) are abstracted to posts and stored in one `MindealPosts` table.


```json
{
    "id" String: "335a76b9-9932-44c2-9d92-ae34aee1a17c",
    "title" String: "Burberry香水线上3折起",
    "subtitle" String: "低至三折+买一送一",
    "price" String: "30",
    "currency" String: "",
    "banner_images" String Set: ["https://mindeal-cms-test.s3.amazonaws.com/favicon.ico", "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico", "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"],
    "payment_method" String Set: ["wechatpay", "alipay"],
    "is_china_delivery" Boolran: true,
    "coupons" String Set: ["DEALMOON4JULY", "DEALMOON4JULY"],
    "content" String: "<!DOCTYPE html><html lang="en"><head> <meta charset="UTF-8"> <meta name="viewport" content="width=device-width, initial-scale=1.0"> <meta http-equiv="X-UA-Compatible" content="ie=edge"> <title>Document</title></head><body> </body></html>",
    "showed_favorites" Number: 12,
    "actual_favorites" Number: 0,
    "comments" List: [
        {
            "id": "7db3326e-3860-43be-b647-0109c48b19a6",
            "author": {
                "id": "2d456a54-672f-4bb2-bbe4-838605b1bb8b",
                "name": "AssWeCan",
                "avatar": "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"
            },
            "content": "卧槽你说很有道理！",
            "parent_id": "00a71a22-ca20-4b6d-abb7-ada2f56c50f2",
            "posted_at": 1562383349
        }
    ],
    "purchase_url" String: "https://goo.gl"
}
```

## Attributes list

- [`id`](#id)
- [`title`](#title)
- [`subtitle`](#subtitle)
- [`price`](#price)
- [`banner_images`](#banner_images)
- [`payment_method`](#payment_method)
- [`is_china_delivery`](#is_china_delivery)
- [`coupons`](#coupons)
- [`content`](#content)
- [`showed_favorites`](#showed_favorites)
- [`actual_favorites`](#actual_favorites)
- [`comments`](#comments)
- [`purchase_url`](#purchase_url)

## Attributes details
---
### `id`
---
#### Type
`String`
#### Description
Uniquely generated UUID of a post.

---
### `title`
---
#### Type
`String`
#### Description
The title of a post.

---
### `subtitle`
---
#### Type
`String`
#### Description
The subtitle of a post.

---
### `price`
---
#### Type
`String`
#### Description
The price of a post.

---
### `banner_images`
---
#### Type
`String Set`
#### Description
The array of s3 links for banner images. Currently there has at most five banner images for each post.

---
### `payment_method`
---
#### Type
`String Set`
#### Description
The array of supported payment methods. Currently there has **TWO** possible values.
- `wechatpay`: Wechat Payment
- `alipay`: Alipay

---
### `is_china_delivery`
---
#### Type
`Boolean`
#### Description
Indicates if it's China shipping.

---
### `coupons`
---
#### Type
`String Set`
#### Description
The array of coupons

---
### `content`
---
#### Type
`String`
#### Description
The content HTML page.

---
### `showed_favorites`
---
#### Type
`Number`
#### Description
Number of favorites to be showed

---
### `actual_favorites`
---
#### Type
`Number`
#### Description
Real number of favorites.

---
### `comments`
---
#### Type
`List`
#### Description
The comments is a `List` of `Map`s containing the following attributes snapshoted from `MindealComments` and `MindealUsers` table.
- `id`: UUID of the comment
- `author`: a Map containing user information:
    - `id`: UUID of the user
    - `name`: User's name
    - `avatar`: User's profile image s3 link
- `content`: full comment text
- `parent_id`: UUID of parent comment
- `posted_at`: epoch time when posted

---
### `purchase_url`
---
#### Type
`String`
#### Description
Where to buy(We will make money here!)