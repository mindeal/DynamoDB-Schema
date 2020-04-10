# 折扣字段描述

## `title` 标题
折扣的标题，由用户填写

## `subtitle` 副标题
折扣的副标题，由用户填写

## `category` 分类
折扣所属于的分类，由用户从已有的分类当中选择

## `createdAt` 发布时间
折扣发布的时间，由用户从日期选择器里选择，若没有选择，则使用用户点击发布时候的时间
使用UTC时间，格式为`2020-04-06T14:00:30.072Z`

## `paymentMethod` 支付方式
折扣支持的支付方式，由用户从`alipay(支付宝)`,`wechatpay(微信支付)`中添加，可以为空，或者多个。

## `isDeliverToChina` 海淘直邮
折扣商品是否支持直邮，由用户打勾选择，默认为`false`打勾为`true`

## `bannerImages` 横幅图片
由用户上传的banner图片，最多5张

## `image` 缩略图片
由用户上传的折扣在list显示时用的缩略图

## `content` 折扣详情
由用户在markdown编辑器中填写

## `purchaseURL` 购买链接
折扣的购买链接，由用户填写

## `brands` 品牌

由用户在已有的品牌列表中选取添加，可为空或者多个

### `brand.id` 品牌id
由用户在品牌列表中选择后自动填充

### `brand.image` 品牌图片
由用户在品牌列表中选择后自动填充
### `brand.name` 品牌名称
由用户在品牌列表中选择后自动填充
## `popularItems` 精选商品

由用户添加的精选商品，可为空或者多个，有以下属性

### `popularItems.title` 商品标题
精选商品的标题，由用户填写

### `popularItems.purchaseURL` 购买链接
精选商品的购买链接，由用户填写

### `popularItems.image` 购买链接
精选商品的缩略图，由用户上传