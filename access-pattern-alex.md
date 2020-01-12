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

* Get latest deals overall
* Get hottest deals - hot deals are defined by editor manually in CMS
* Get latest deals in different categories.

## Deal Page

* Top section contains banner images
* Black text is title of deal, left blue bubble is label
* Red text is subtitle
* three icons are China delivery (Optional), and supported payment methods
* Next is coupon area containing coupon code and corresponding description
* Markdown text area is deal description
* Next part is editor choice single product of the deal (Optional)
* Last part contains all brands relating to the deal (Optional)

### Sample payload

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
