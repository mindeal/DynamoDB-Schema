# App

## Deal

1. [Get a deal with details](#Get-a-deal-with-details)
1. Get `n` latest deals overall
1. Get `n` latest deals in `category`
1. Get `n` latest deals in `brand`
1. [Get hottest deals](#get-hottest-deals)

### Get a deal with details
`get: table: pk: table-pk = id, sk = "deal"`

### Get `n` latest deals overall
`query: gsi2: pk: table-sk = "deal", sk: published_at < now, ScanIndexForward = true, Limit = n`

### Get `n` latest deals in `category`
`query: gsi2: pk: table-sk = "category-id", sk: published_at < deal#now, ScanIndexForward = true, Limit = n`

### Get `n` latest deals in `brand`
`query: gsi2: pk: table-sk = "brand-id", sk: published_at < deal#now, ScanIndexForward = true, Limit = n`

### Get hottest deals
`query: gsi3: pk: table-sk = "deal", sk: is_hot = true`(Sparse Index)


## Article
1. [Get an article with details](#Get-an-article-with-details)
1. Get `n` latest articles overall
1. Get `n` latest articles in `category`
1. Get `n` latest articles in `brand`
1. [Get `hottest` articles](#get-hottest-articles)

### Get an article with details
`get: table: pk: table-pk = id, sk = "article"`

### Get `n` latest articles overall
`query: gsi2: pk: table-sk = "article", sk: published_at < now, ScanIndexForward = true, Limit = n`

### Get `n` latest articles in `category`
`query: gsi2: pk: table-sk = "category-id", sk: published_at < article#now, ScanIndexForward = true, Limit = n`

### Get `n` latest articles in `brand`
`query: gsi2: pk: table-sk = "brand-id", sk: published_at < article#now, ScanIndexForward = true, Limit = n`

### Get `hottest` articles
`query: gsi3: pk: table-sk = "article", sk: is_hot = true`(Sparse Index)

## Category
1. Get all categories

### Get all categories
`query: gsi1: pk: table-sk = "category"`

## Brand
1. Get all brands A-Z 
1. Get hottest brands

### Get all brands A-Z
`query: gsi1: pk: table-sk = "brand"`(Lambda Sort)

### Get hottest brands
`query: gsi2: pk: table-sk = "brand", sk: is_hot = true`(Sparse Index)

## Comment


# CMS

## Deal

1. Get a single deal with details
1. Get list of all categories
1. Get list of all brands
1. Get hottest deals
1. Get hottest brands
1. Get lastest deals
1. Get lastest articles
1. Get deals by categories and by time
1. Get comment by popularity
1. Get comment by time(old <-> new)
1. User liked
1. User favorited
1. Notifications by user
1. Official notification