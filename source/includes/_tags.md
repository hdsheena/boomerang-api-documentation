# Tags

Tags are designed to find specific resources faster. They can be added to the following resources by supplying a `tag_list`.

- [Order](#orders)
- [Customer](#customers)
- [Product group](#product_groups)
- [Bundle](#bundles)
- [Document](#documents)

## Fields
Every tag has the following fields:

Name | Description
- | -
`id` | **Uuid** `readonly`<br>
`for` | **String** `writeonly`<br>The resource to show the tag counts for. One of `Order`, `Customer`, `ProductGroup`, `Bundle`, `Document`
`name` | **String** <br>Name of the tag
`count` | **Integer** <br>Total count


## Listing tags



> How to fetch a list of tags with their counts:

```shell
  curl --request GET \
    --url 'https://example.booqable.com/api/boomerang/tags?filter%5Bfor%5D=Order' \
    --header 'content-type: application/json' \
```

> A 200 status response looks like this:

```json
  {
  "data": [
    {
      "id": "5087b2b4-f80d-48ce-8b94-cceb76e2c5b8",
      "type": "tags",
      "attributes": {
        "name": "vip",
        "count": 1
      }
    },
    {
      "id": "3d96767c-7d62-4d4a-bed0-6b85af2eb608",
      "type": "tags",
      "attributes": {
        "name": "webshop",
        "count": 3
      }
    }
  ],
  "meta": {}
}
```

### HTTP Request

`GET /api/boomerang/tags`

### Request params

This request accepts the following parameters:

Name | Description
- | -
`include` | **String** <br>List of comma seperated relationships `?include=`
`fields[]` | **Array** <br>List of comma seperated fields to include `?fields[tags]=id,created_at,updated_at`
`filter` | **Hash** <br>The filters to apply `?filter[created_at][gte]=2022-09-30T11:57:11Z`
`sort` | **String** <br>How to sort the data `?sort=-created_at`
`meta` | **Hash** <br>Metadata to send along `?meta[total][]=count`
`page[number]` | **String** <br>The page to request
`page[size]` | **String** <br>The amount of items per page (max 100)


### Filters

This request can be filtered on:

Name | Description
- | -
`for` | **String** <br>`eq`


### Meta

Results can be aggregated on:

Name | Description
- | -
`total` | **Array** <br>`count`


### Includes

This request does not accept any includes