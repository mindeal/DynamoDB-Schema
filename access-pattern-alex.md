# App Mock Up Explanation

## Main Page

![main-page.png](https://i.loli.net/2020/01/12/bnyfXW27sch4Tei.png)

---

![main-page-scroll-down.png](https://i.loli.net/2020/01/12/J38SWRZeF9BdGws.png)

* The top horizontal scroll parts are banners. Each one of them could link to either deal detail page or article detail page.
* Ten icons arranged in two rows are categories. There are hardcoded
* HOT section contains the hottest deals
* NEW section contains the latest deals

### Access Patterns

* Get latest deals and articles overall
* Get hottest deals - hot deals are defined by editor manually in CMS
* Get latest deals in different categories.

## Deal Page

![产品详情页 - 切图备份 4.png](https://i.loli.net/2020/01/14/NgJar9EvyzeLbmG.png)
* Top section contains banner images
* Black text is title of deal, left blue bubble is label
* Red text is subtitle
* three icons are China delivery (Optional), and supported payment methods
* Next is coupon area containing coupon code and corresponding description
* Markdown text area is deal description
* Next part is editor choice single product of the deal (Optional)
* Last part contains all brands relating to the deal (Optional)
* The bottom row contains three parts, from left to right, number of comments, number of likes, and purchase url.

### Deal sample payload

```json
{
    "title (String) (required)": "Macy’s 20% OFF",
    "subtitle (String) (required)": "Burberry, Chanel",
    "bannerImages (String Set)": [
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"
    ],
    "paymentMethod (String Set)": [
        "wechatpay",
        "alipay"
    ],
    "label (String)": "exclusive",
    "isDeliverToChina (Boolean)": true,
    "coupons (List)": [
        {
            "code": "AIR5",
            "description": "$5OFF$55"
        },
        {
            "code": "AIR10",
            "description": "$10OFF$100"
        }
    ],
    "body (String) (required)": "https://s3.amazonaws.com/www.mindeal.com/index.html",
    "totalLike (Number) (required)": 10,
    "totalComment (Number) (required)": 10,
    "purchaseUrl (String)": "https://goo.gl",
    "publishedAt (String) (required)": "deal-1567121541828",
    "popularItems (List)": [
        {
            "title": "小棕瓶",
            "thumbnail": "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
            "purchaseUrl": "https://goo.gl"
        },
        {
            "title": "神仙水",
            "thumbnail": "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
            "purchaseUrl": "https://goo.gl"
        }
    ],
    "brands (List)": [
        {
            "id": "brand-2d456a54-672f-4bb2-bbe4-838605b1bb8b",
            "brand": "Jo Malone",
            "thumbnail": "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"
        },
        {
            "id": "brand-2d456a54-672f-4bb2-bbe4-838605b1bb8b",
            "brand": "Jo Malone",
            "thumbnail": "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"
        }
    ]
}

```

The last category in main page is Shipping to China which is actually not a "category" if we use a [sparse indexes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-indexes-general-sparse-indexes.html) to indicate this value.


## Article Page

![品牌模块 - 切图 _1_.png](https://i.loli.net/2020/01/21/tSBbI1jgAhPGkiL.png)

The first line with arrow at right is "Navigate to all brands" to following page

The second part contains hot brands which is set by editors in CMS

The rests(scrolling down) are lasted articles wrote by editors.

### Article sample payload
```json
{
    "title (String) (required)": "Macy’s 20% OFF",
    "subtitle (String) (required)": "Burberry, Chanel",
    "bannerImages (String Set)": [
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"
    ],
    "body (String) (required)": "https://s3.amazonaws.com/www.mindeal.com/index.html",
    "totalLike (Number) (required)": 10,
    "totalComment (Number) (required)": 10
}

```

Click "Navigate to all brands" will lead to all brands page

![全部品牌  - 切图 _1_.png](https://i.loli.net/2020/01/21/S9vTxPVgiImEhar.png)

There are the all brand sorting alphabetically. Each brand can be clicked and it leads to its brand description page.

![品牌详情页  - 切图.png](https://i.loli.net/2020/01/21/lCKjch1TsyJwpgM.png)

### Brand sample payload
```json
{
    "brandName": "Gucci",
    "bannerImages (String Set)": [
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico",
        "https://mindeal-cms-test.s3.amazonaws.com/favicon.ico"
    ],
    "body (String) (required)": "https://s3.amazonaws.com/www.mindeal.com/index.html",
    "officialUrl": "www.example.com"
}

```

## Notification Page

![消息模块 - 切图.png](https://i.loli.net/2020/01/29/3b7By8OTdqLQJ6p.png)

There are two kinds of notifications.

The first one is message sent by Editor. It is all text based, may contain links to certain article or deal.

The second kind is notification when someone reply user's comment.