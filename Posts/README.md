# Posts

All kinds of posts(Deals and Articles) are abstracted to posts and stored in one `MindealPosts` table.

## Attributes list

### Required
- [`id`](#id)

### Optional

#### Deals
- [`title`](#title)
- [`banner_images`](#banner_images)
- [`content`](#content)
- [`showed_favorites`](#showed_favorites)
- [`comments`](#comments)


#### Articles

- [`title`](#title)
- [`subtitle`](#subtitle)
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
`Number`
#### Description
The current price, after discount of a post.

---
### `List_price`
---
#### Type
`Number`
#### Description
The original price, before discount of a post.

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
`List`
#### Description
The List of couples
- `code`: String, the coupon code
- `description`: String, coupon description

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
### `total_comments`
---
#### Type
`Number`
#### Description
Number of total comments.

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

---
### `popular_items`
---
#### Type
`List`
#### Description
List of popular items relating to the post.
- `title`: String, short item description
- `image`: s3 image link
- `price`: current price, after discount price
- `list_price`: original price, before discount price