# Photos

Photos are displayed on documents and in the online store to let customers see how products look.

## Endpoints
`GET /api/boomerang/photos`

`GET /api/boomerang/photos/{id}`

`POST /api/boomerang/photos`

`PUT /api/boomerang/photos/{id}`

`DELETE /api/boomerang/photos/{id}`

## Fields
Every photo has the following fields:

Name | Description
- | -
`id` | **Uuid** `readonly`<br>Primary key
`created_at` | **Datetime** `readonly`<br>When the resource was created
`updated_at` | **Datetime** `readonly`<br>When the resource was last updated
`photo_base64` | **String** `writeonly`<br>Base64 encoded photo
`remote_photo_url` | **String** `writeonly`<br>Url to an image on the web
`original_url` | **String** `readonly`<br>Url to original stored image
`large_url` | **String** `readonly`<br>Url to large stored image (max 500x500)
`xlarge_url` | **String** `readonly`<br>Url to xlarge stored image (max 2000x2000)
`coordinates` | **Hash**<br>Focalpoint coordinates (`{ x: 10, y: 100 }`). To ensure that a key part of an image stays visible, you can set the image's focal point. The focal point sets the focus of an image, giving you control over where the image is centered.
`preview` | **String** `readonly`<br>Base64 encoded preview
`position` | **Integer**<br>Which position the photo has in the album
`owner_id` | **Uuid**<br>ID of its owner
`owner_type` | **String**<br>The resource type of the owner. One of `Item`, `ProductGroup`, `Bundle`


## Listing photos

> How to fetch a list of photos:

```shell
  curl --request GET \
    --url 'https://example.booqable.com/api/boomerang/photos' \
    --header 'content-type: application/json' \
```

> A 200 status response looks like this:

```json
  {
  "data": [
    {
      "id": "ca3c0fdc-685e-4497-bb99-4a763420f165",
      "type": "photos",
      "attributes": {
        "created_at": "2021-10-08T09:34:25+00:00",
        "updated_at": "2021-10-08T09:34:25+00:00",
        "original_url": "/uploads/4aa8696926863445edf042d8d7086c4a/photo/photo/ca3c0fdc-685e-4497-bb99-4a763420f165/photo.png",
        "large_url": "/uploads/4aa8696926863445edf042d8d7086c4a/photo/photo/ca3c0fdc-685e-4497-bb99-4a763420f165/large_photo.jpg",
        "xlarge_url": "/uploads/4aa8696926863445edf042d8d7086c4a/photo/photo/ca3c0fdc-685e-4497-bb99-4a763420f165/xlarge_photo.jpg",
        "coordinates": {
          "x": "0.00",
          "y": "0.00"
        },
        "preview": "iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAMAAADzN3VRAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABVlBMVEX////+///4/v/a8v+H3P5h2P584/7Q9v/5/P+02v9Xuf02tv0vvv0pxv080v2c6v70/f/u8v+ZvP5Vnf5Jof5Eqv0+sf03uf0vwf0tyf1x3/7j+f/l5v+Pnf9ihf9cjf9Wlf9Qnf9JpP5CrP08s/01u/0tw/1Z1f3T9P/k3f+Of/JlYtxcZc1WaclQb8xUgdxfm/ZRof5Gpf5Brv07tv0xvf1Qzf3N8v/q4fqNadRgRLBZR6NTSqFRUKJ2fLe8xN7h6PjE2/98tP5Nof5Fp/0/sP02t/1Vyf3a9P/6+PygesllM6RiOqJdPKJqVaytqNPx8fjy9/+tzv9gpf5Iof46sf14zv72/P/p3fF9OqtqKKJsNaaRcb7a0+rX5v+Dtf5Rnv5Fov5OsP3b8P/28fquf8qdZ7/JsN338/r1+P+91v+Dtv6OxP7v+P/9+/78+v36/P/7/P8g+7k+AAAAAWJLR0QAiAUdSAAAAAd0SU1FB+UKCAkiGclRxbAAAACfSURBVCjPY2AY6oCRiRG7BDMLKxs7FnEOTi5uHl4+fgF0CUEhYRFRMXEJSSlpVAkZWTl5BUUlZRVVNXUNZAlNLW0dXT19A0MjYxNTM3OEhIWllbWNrZ29g6OTs4urm7sHTMLTy9vH188/AMgMDAoOEQ0NC4fKRERGRcfEQjlx8QmJSclQTkpqWnoG3OjMrOycXBgnLx/FoQWFAx0b5AMATrUZQFRVtxIAAAAldEVYdGRhdGU6Y3JlYXRlADIwMjEtMTAtMDhUMDk6MzQ6MjUrMDA6MDAKQUJyAAAAJXRFWHRkYXRlOm1vZGlmeQAyMDIxLTEwLTA4VDA5OjM0OjI1KzAwOjAwexz6zgAAAABJRU5ErkJggg==",
        "position": 1,
        "owner_id": "f7bdb645-20c6-4d30-b204-3a906f600e4c",
        "owner_type": "ProductGroup"
      }
    }
  ],
  "meta": {}
}
```


### HTTP Request

`GET /api/boomerang/photos`

### Request params

This request accepts the following paramaters:

Name | Description
- | -
`include` | **String**<br>List of comma seperated relationships `?include=`
`fields[]` | **Array**<br>List of comma seperated fields to include `?fields[photos]=id,created_at,updated_at`
`filter` | **Hash**<br>The filters to apply `?filter[created_at][gte]=2021-10-08T09:34:23Z`
`sort` | **String**<br>How to sort the data `?sort=-created_at`
`meta` | **Hash**<br>Metadata to send along `?meta[total][]=count`
`page[number]` | **String**<br>The page to request
`page[per]` | **String**<br>The amount of items per page (max 100)


### Filters

This request can be filtered on:

Name | Description
- | -
`id` | **Uuid**<br>`eq`, `not_eq`
`created_at` | **Datetime**<br>`eq`, `not_eq`, `gt`, `gte`, `lt`, `lte`
`updated_at` | **Datetime**<br>`eq`, `not_eq`, `gt`, `gte`, `lt`, `lte`
`owner_id` | **Uuid**<br>`eq`, `not_eq`
`owner_type` | **String**<br>`eq`, `not_eq`, `eql`, `not_eql`, `prefix`, `not_prefix`, `suffix`, `not_suffix`, `match`, `not_match`


### Meta

Results can be aggregated on:

Name | Description
- | -
`total` | **Array**<br>`count`


### Includes

This request does not accept any includes
## Fetching a photo

> How to fetch a photo:

```shell
  curl --request GET \
    --url 'https://example.booqable.com/api/boomerang/photos/816e57b5-6f0d-4560-bc62-ab971bb2096a' \
    --header 'content-type: application/json' \
```

> A 200 status response looks like this:

```json
  {
  "data": {
    "id": "816e57b5-6f0d-4560-bc62-ab971bb2096a",
    "type": "photos",
    "attributes": {
      "created_at": "2021-10-08T09:34:26+00:00",
      "updated_at": "2021-10-08T09:34:26+00:00",
      "original_url": "/uploads/5b6f99068471ab9f85149ab2b897e9cb/photo/photo/816e57b5-6f0d-4560-bc62-ab971bb2096a/photo.png",
      "large_url": "/uploads/5b6f99068471ab9f85149ab2b897e9cb/photo/photo/816e57b5-6f0d-4560-bc62-ab971bb2096a/large_photo.jpg",
      "xlarge_url": "/uploads/5b6f99068471ab9f85149ab2b897e9cb/photo/photo/816e57b5-6f0d-4560-bc62-ab971bb2096a/xlarge_photo.jpg",
      "coordinates": {
        "x": "0.00",
        "y": "0.00"
      },
      "preview": "iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAMAAADzN3VRAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABVlBMVEX////+///4/v/a8v+H3P5h2P584/7Q9v/5/P+02v9Xuf02tv0vvv0pxv080v2c6v70/f/u8v+ZvP5Vnf5Jof5Eqv0+sf03uf0vwf0tyf1x3/7j+f/l5v+Pnf9ihf9cjf9Wlf9Qnf9JpP5CrP08s/01u/0tw/1Z1f3T9P/k3f+Of/JlYtxcZc1WaclQb8xUgdxfm/ZRof5Gpf5Brv07tv0xvf1Qzf3N8v/q4fqNadRgRLBZR6NTSqFRUKJ2fLe8xN7h6PjE2/98tP5Nof5Fp/0/sP02t/1Vyf3a9P/6+PygesllM6RiOqJdPKJqVaytqNPx8fjy9/+tzv9gpf5Iof46sf14zv72/P/p3fF9OqtqKKJsNaaRcb7a0+rX5v+Dtf5Rnv5Fov5OsP3b8P/28fquf8qdZ7/JsN338/r1+P+91v+Dtv6OxP7v+P/9+/78+v36/P/7/P8g+7k+AAAAAWJLR0QAiAUdSAAAAAd0SU1FB+UKCAkiGlBYlAoAAACfSURBVCjPY2AY6oCRiRG7BDMLKxs7FnEOTi5uHl4+fgF0CUEhYRFRMXEJSSlpVAkZWTl5BUUlZRVVNXUNZAlNLW0dXT19A0MjYxNTM3OEhIWllbWNrZ29g6OTs4urm7sHTMLTy9vH188/AMgMDAoOEQ0NC4fKRERGRcfEQjlx8QmJSclQTkpqWnoG3OjMrOycXBgnLx/FoQWFAx0b5AMATrUZQFRVtxIAAAAldEVYdGRhdGU6Y3JlYXRlADIwMjEtMTAtMDhUMDk6MzQ6MjYrMDA6MDA7qVjvAAAAJXRFWHRkYXRlOm1vZGlmeQAyMDIxLTEwLTA4VDA5OjM0OjI2KzAwOjAwSvTgUwAAAABJRU5ErkJggg==",
      "position": 1,
      "owner_id": "f621b9f2-30c3-41f5-9029-55ba28590fee",
      "owner_type": "ProductGroup"
    }
  },
  "meta": {}
}
```


### HTTP Request

`GET /api/boomerang/photos/{id}`

### Request params

This request accepts the following paramaters:

Name | Description
- | -
`include` | **String**<br>List of comma seperated relationships `?include=`
`fields[]` | **Array**<br>List of comma seperated fields to include `?fields[photos]=id,created_at,updated_at`


### Includes

This request accepts the following includes:

`owner`






## Creating a photo

> How to create a photo:

```shell
  curl --request POST \
    --url 'https://example.booqable.com/api/boomerang/photos' \
    --header 'content-type: application/json' \
    --data '{
      "data": {
        "type": "photos",
        "attributes": {
          "owner_id": "be11736d-719a-472a-8f1a-bddf8fecdc66",
          "owner_type": "ProductGroup",
          "photo_base64": "data:image/png;base64,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\n"
        }
      }
    }'
```

> A 201 status response looks like this:

```json
  {
  "data": {
    "id": "7ccfc308-2086-4cc2-92a4-35e4ab0fde42",
    "type": "photos",
    "attributes": {
      "created_at": "2021-10-08T09:34:27+00:00",
      "updated_at": "2021-10-08T09:34:27+00:00",
      "original_url": "/uploads/084001bffae380d81fcad8d75486c174/photo/photo/7ccfc308-2086-4cc2-92a4-35e4ab0fde42/photo.png",
      "large_url": "/uploads/084001bffae380d81fcad8d75486c174/photo/photo/7ccfc308-2086-4cc2-92a4-35e4ab0fde42/large_photo.jpg",
      "xlarge_url": "/uploads/084001bffae380d81fcad8d75486c174/photo/photo/7ccfc308-2086-4cc2-92a4-35e4ab0fde42/xlarge_photo.jpg",
      "coordinates": {
        "x": 0,
        "y": 0
      },
      "preview": "iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAMAAADzN3VRAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABVlBMVEX////+///4/v/a8v+H3P5h2P584/7Q9v/5/P+02v9Xuf02tv0vvv0pxv080v2c6v70/f/u8v+ZvP5Vnf5Jof5Eqv0+sf03uf0vwf0tyf1x3/7j+f/l5v+Pnf9ihf9cjf9Wlf9Qnf9JpP5CrP08s/01u/0tw/1Z1f3T9P/k3f+Of/JlYtxcZc1WaclQb8xUgdxfm/ZRof5Gpf5Brv07tv0xvf1Qzf3N8v/q4fqNadRgRLBZR6NTSqFRUKJ2fLe8xN7h6PjE2/98tP5Nof5Fp/0/sP02t/1Vyf3a9P/6+PygesllM6RiOqJdPKJqVaytqNPx8fjy9/+tzv9gpf5Iof46sf14zv72/P/p3fF9OqtqKKJsNaaRcb7a0+rX5v+Dtf5Rnv5Fov5OsP3b8P/28fquf8qdZ7/JsN338/r1+P+91v+Dtv6OxP7v+P/9+/78+v36/P/7/P8g+7k+AAAAAWJLR0QAiAUdSAAAAAd0SU1FB+UKCAkiGydfpJwAAACfSURBVCjPY2AY6oCRiRG7BDMLKxs7FnEOTi5uHl4+fgF0CUEhYRFRMXEJSSlpVAkZWTl5BUUlZRVVNXUNZAlNLW0dXT19A0MjYxNTM3OEhIWllbWNrZ29g6OTs4urm7sHTMLTy9vH188/AMgMDAoOEQ0NC4fKRERGRcfEQjlx8QmJSclQTkpqWnoG3OjMrOycXBgnLx/FoQWFAx0b5AMATrUZQFRVtxIAAAAldEVYdGRhdGU6Y3JlYXRlADIwMjEtMTAtMDhUMDk6MzQ6MjcrMDA6MDCd3lNbAAAAJXRFWHRkYXRlOm1vZGlmeQAyMDIxLTEwLTA4VDA5OjM0OjI3KzAwOjAw7IPr5wAAAABJRU5ErkJggg==",
      "position": 2,
      "owner_id": "be11736d-719a-472a-8f1a-bddf8fecdc66",
      "owner_type": "ProductGroup"
    }
  },
  "meta": {}
}
```


### HTTP Request

`POST /api/boomerang/photos`

### Request params

This request accepts the following paramaters:

Name | Description
- | -
`include` | **String**<br>List of comma seperated relationships `?include=`
`fields[]` | **Array**<br>List of comma seperated fields to include `?fields[photos]=id,created_at,updated_at`


### Request body

This request accepts the following body:

Name | Description
- | -
`data[attributes][photo_base64]` | **String**<br>Base64 encoded photo
`data[attributes][remote_photo_url]` | **String**<br>Url to an image on the web
`data[attributes][coordinates]` | **Hash**<br>Focalpoint coordinates (`{ x: 10, y: 100 }`). To ensure that a key part of an image stays visible, you can set the image's focal point. The focal point sets the focus of an image, giving you control over where the image is centered.
`data[attributes][position]` | **Integer**<br>Which position the photo has in the album
`data[attributes][owner_id]` | **Uuid**<br>ID of its owner
`data[attributes][owner_type]` | **String**<br>The resource type of the owner. One of `Item`, `ProductGroup`, `Bundle`


### Includes

This request accepts the following includes:

`owner`






## Updating a photo

> How to update a photo:

```shell
  curl --request PUT \
    --url 'https://example.booqable.com/api/boomerang/photos/44da0e44-dd07-4184-9894-f07324b7a4f2' \
    --header 'content-type: application/json' \
    --data '{
      "data": {
        "id": "44da0e44-dd07-4184-9894-f07324b7a4f2",
        "type": "photos",
        "attributes": {
          "coordinates": {
            "x": 10,
            "y": 100
          }
        }
      }
    }'
```

> A 200 status response looks like this:

```json
  {
  "data": {
    "id": "44da0e44-dd07-4184-9894-f07324b7a4f2",
    "type": "photos",
    "attributes": {
      "created_at": "2021-10-08T09:34:27+00:00",
      "updated_at": "2021-10-08T09:34:27+00:00",
      "original_url": "/uploads/9686df4cb945b70baf4a556250378f78/photo/photo/44da0e44-dd07-4184-9894-f07324b7a4f2/photo.png",
      "large_url": "/uploads/9686df4cb945b70baf4a556250378f78/photo/photo/44da0e44-dd07-4184-9894-f07324b7a4f2/large_photo.jpg",
      "xlarge_url": "/uploads/9686df4cb945b70baf4a556250378f78/photo/photo/44da0e44-dd07-4184-9894-f07324b7a4f2/xlarge_photo.jpg",
      "coordinates": {
        "x": 10,
        "y": 100
      },
      "preview": "iVBORw0KGgoAAAANSUhEUgAAABkAAAAZCAMAAADzN3VRAAAABGdBTUEAALGPC/xhBQAAACBjSFJNAAB6JgAAgIQAAPoAAACA6AAAdTAAAOpgAAA6mAAAF3CculE8AAABVlBMVEX////+///4/v/a8v+H3P5h2P584/7Q9v/5/P+02v9Xuf02tv0vvv0pxv080v2c6v70/f/u8v+ZvP5Vnf5Jof5Eqv0+sf03uf0vwf0tyf1x3/7j+f/l5v+Pnf9ihf9cjf9Wlf9Qnf9JpP5CrP08s/01u/0tw/1Z1f3T9P/k3f+Of/JlYtxcZc1WaclQb8xUgdxfm/ZRof5Gpf5Brv07tv0xvf1Qzf3N8v/q4fqNadRgRLBZR6NTSqFRUKJ2fLe8xN7h6PjE2/98tP5Nof5Fp/0/sP02t/1Vyf3a9P/6+PygesllM6RiOqJdPKJqVaytqNPx8fjy9/+tzv9gpf5Iof46sf14zv72/P/p3fF9OqtqKKJsNaaRcb7a0+rX5v+Dtf5Rnv5Fov5OsP3b8P/28fquf8qdZ7/JsN338/r1+P+91v+Dtv6OxP7v+P/9+/78+v36/P/7/P8g+7k+AAAAAWJLR0QAiAUdSAAAAAd0SU1FB+UKCAkiGydfpJwAAACfSURBVCjPY2AY6oCRiRG7BDMLKxs7FnEOTi5uHl4+fgF0CUEhYRFRMXEJSSlpVAkZWTl5BUUlZRVVNXUNZAlNLW0dXT19A0MjYxNTM3OEhIWllbWNrZ29g6OTs4urm7sHTMLTy9vH188/AMgMDAoOEQ0NC4fKRERGRcfEQjlx8QmJSclQTkpqWnoG3OjMrOycXBgnLx/FoQWFAx0b5AMATrUZQFRVtxIAAAAldEVYdGRhdGU6Y3JlYXRlADIwMjEtMTAtMDhUMDk6MzQ6MjcrMDA6MDCd3lNbAAAAJXRFWHRkYXRlOm1vZGlmeQAyMDIxLTEwLTA4VDA5OjM0OjI3KzAwOjAw7IPr5wAAAABJRU5ErkJggg==",
      "position": 1,
      "owner_id": "b843d662-56d6-4e4e-9b44-b21c7e8bd255",
      "owner_type": "ProductGroup"
    }
  },
  "meta": {}
}
```


### HTTP Request

`PUT /api/boomerang/photos/{id}`

### Request params

This request accepts the following paramaters:

Name | Description
- | -
`include` | **String**<br>List of comma seperated relationships `?include=`
`fields[]` | **Array**<br>List of comma seperated fields to include `?fields[photos]=id,created_at,updated_at`


### Request body

This request accepts the following body:

Name | Description
- | -
`data[attributes][photo_base64]` | **String**<br>Base64 encoded photo
`data[attributes][remote_photo_url]` | **String**<br>Url to an image on the web
`data[attributes][coordinates]` | **Hash**<br>Focalpoint coordinates (`{ x: 10, y: 100 }`). To ensure that a key part of an image stays visible, you can set the image's focal point. The focal point sets the focus of an image, giving you control over where the image is centered.
`data[attributes][position]` | **Integer**<br>Which position the photo has in the album
`data[attributes][owner_id]` | **Uuid**<br>ID of its owner
`data[attributes][owner_type]` | **String**<br>The resource type of the owner. One of `Item`, `ProductGroup`, `Bundle`


### Includes

This request accepts the following includes:

`owner`






## Deleting a photo

> How to delete a photo:

```shell
  curl --request DELETE \
    --url 'https://example.booqable.com/api/boomerang/photos/8b181483-f8e5-4b07-8c39-d450bcb2a16b' \
    --header 'content-type: application/json' \
```

> A 200 status response looks like this:

```json
  {
  "meta": {}
}
```


### HTTP Request

`DELETE /api/boomerang/photos/{id}`

### Request params

This request accepts the following paramaters:

Name | Description
- | -
`include` | **String**<br>List of comma seperated relationships `?include=`
`fields[]` | **Array**<br>List of comma seperated fields to include `?fields[photos]=id,created_at,updated_at`


### Includes

This request does not accept any includes