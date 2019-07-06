# Posts
1. ~~How do to store shipping method~~
2. ~~Shall we store content HTML to S3~~
3. ~~Favorites should be a number or string~~
4. ~~For performance's sake, `content` should store the latest snapshot of comments(lambda's job to update)~~
5. Mechanism of showing favorites number
6. Max length of title/subtitle?
7. Do we need price and how do we store price?
8. Should comment store the lastest or oldest and in order issue.

# Comments
1. ~~One big table or separated table for different types of post?~~ YES
    - ~~One big table: How do we identify its parent post~~
2. ~~Is UUID unique cross the tables~~ YES

# Users
1. ~~Duplicate Congnito data in DynamoDB~~ YES
2. ~~Shall we log all profile changes~~ NO
    - ~~`prev_avatars` & `prev_location`~~

# Extra
- ~~Can we combine all different type of post(deals & articles for now) into one table?~~ YES
    - Partition & Sort key issue
- ~~Do we need category table?~~ YES
- ~~Figuring out the pricing~~