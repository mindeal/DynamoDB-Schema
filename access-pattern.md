# App

## Deal

1. [Get a single deal with details](#Get-a-deal-with-details)
1. [Get n latest deals overall](#Get-n-latest-deals-overall)
1. [Get n latest deals belonging to a category](#Get-n-latest-deals-belonging-to-a-category)
1. [Get n latest deals belonging to a brand](#Get-n-latest-deals-belonging-to-a-brand)
1. [Get hottest deals](#get-hottest-deals)

### Get a deal with details
点击deal进入单个deal的详情页
```
Method: Get
Table: Main table
pk: 9edbc112-c07f-4800-98dd-040f394379c7
sk: deal.rand(0, 14)
```
We calculate "`rand(0, 14)`" by using the `time_low` part of deal uuid.
```
ItemsPerRCU = 8KB / 500B = 16
PartitionMaxReadRate = 3K * ItemsPerRCU = 48K
N = (10 * 24 * 365 * 5) / 48K = 9 -> 15
```

Sample Code:
```javascript
function getShardingNumberFromUUID(uuid) {
  const timeLow = uuid.split('-')[0];
  const timeLowNumber = parseInt(timeLow, 16);
  const shardingNumber = timeLowNumber % 15;
  return shardingNumber;
}
getShardingNumberFromUUID('281d5b08-248c-4bdf-a790-10de2da4a2fb');
```

### Get n latest deals overall
```
Method: Query
Table: GSI2
pk: deal.0 to deal.34
sk: publishedAt(staring with deal-) < current_time
ScanIndexForward: true
Limit: n
```
We need to use parallel query `n` deals on every `deal.rand(0, 34)` partition and use lambda to sort and select top `n` from result

### Get n latest deals belonging to a category
```
Method: Query
Table: GSI2
pk: b5e4bf4d-3b5c-4469-a52f-ab8d8c753a0d
sk: publishedAt(staring with deal-) < current_time
ScanIndexForward: true
Limit: n
```

### Get n latest deals belonging to a brand
```
Method: Query
Table: GSI2
pk: a0ae753f-9927-4625-a50c-ed767a9ae3a9
sk: publishedAt(staring with deal-) < current_time
ScanIndexForward: true
Limit: n
```

### Get hottest deals
```

query: gsi3: pk: table-sk = "deal", sk: isPopular = true (Sparse Index: checking existence)
```


## Article
1. [Get an article with details](#Get-an-article-with-details)
1. [Get n latest articles from overall](#Get-n-latest-articles-from-overall)
1. [Get n latest articles belonging to a category](#Get-n-latest-articles-belonging-to-a-category)
1. [Get n latest articles belonging to a brand](#Get-n-latest-articles-belonging-to-a-brand)
1. [Get hottest articles](#get-hottest-articles)

### Get an article with details
```
get: table: pk: table-pk = id, sk = "article"
```

### Get n latest articles from overall
```
query: gsi2: pk: table-sk = "article", sk: published_at < now, ScanIndexForward = true, Limit = n
```

### Get n latest articles belonging to a category
```
query: gsi2: pk: table-sk = "category-id", sk: published_at < article#now, ScanIndexForward = true, Limit = n
```

### Get n latest articles belonging to a brand
```
query: gsi2: pk: table-sk = "brand-id", sk: published_at < article#now, ScanIndexForward = true, Limit = n
```

### Get hottest articles
```
query: gsi3: pk: table-sk = "article", sk: is_hot = true`(Sparse Index)
```

## Category
1. [Get all categories](#Get-all-categories)

### Get all categories
```
query: gsi1: pk: table-sk = "category"
```

## Brand
1. [Get all brands A-Z](#Get-all-brands-A-Z)
1. [Get hottest brands](#Get-hottest-brands)

### Get all brands A-Z
```
query: gsi1: pk: table-sk = "brand"`(Lambda Sort)
```

### Get hottest brands
```
query: gsi2: pk: table-sk = "brand", sk: is_hot = true`(Sparse Index)
```

## Comment


# CMS

## Deal

1. [Save to draft](#Save-to-draft)
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

### Save to draft
