---
share: true
created: 2023-10-26T00:13
updated: 2024-07-27T14:04
---
[[Node với edge được gọi chung là endpoint]]
nodes to get data about a specific object, use edges to get collections of objects on a single object, and use fields to get data about a single object or each object in a collection
## Nodes

A node is an individual object with a unique ID. For example, there are many User node objects, each with a unique ID representing a person on Facebook. Pages, Groups, Posts, Photos, and Comments are just some of the nodes of the Facebook Social Graph.

The following cURL example represents a call to the User node.

```
curl -i -X GET \
  "https://graph.facebook.com/USER-ID?access_token=ACCESS-TOKEN"
```

This request would return the following data by default, formatted using JSON:

```
{
  "name": "Your Name",
  "id": "YOUR-USER-ID"
}
```

### Node Metadata

You can get a list of all fields, including the field name, description, and data type, of a node object, such as a User, Page, or Photo. Send a `GET` request to an object ID and include the `metadata=1` parameter:

```
curl -i -X GET \
  "https://graph.facebook.com/USER-ID?
    metadata=1&access_token=ACCESS-TOKEN"
```

The resulting JSON response will include the `metadata` property that lists all the supported fields for the given node:

```
{
  "name": "Jane Smith",
  "metadata": {
    "fields": [
      {
        "name": "id",
        "description": "The app user's App-Scoped User ID. This ID is unique to the app and cannot be used by other apps.",
        "type": "numeric string"
      },
      {
        "name": "age_range",
        "description": "The age segment for this person expressed as a minimum and maximum age. For example, more than 18, less than 21.",
        "type": "agerange"
      },
      {
        "name": "birthday",
        "description": "The person's birthday.  This is a fixed format string, like `MM/DD/YYYY`.  However, people can control who can see the year they were born separately from the month and day so this string can be only the year (YYYY) or the month + day (MM/DD)",
        "type": "string"
      },
...
```

[](https://developers.facebook.com/docs/graph-api/overview#)

## /me

The `/me` node is a special endpoint that translates to the object ID of the person or Page whose access token is currently being used to make the API calls. If you had a User access token, you could retrieve a User's name and ID by using:

```
curl -i -X GET \
  "https://graph.facebook.com/me?access_token=ACCESS-TOKEN"
```

[](https://developers.facebook.com/docs/graph-api/overview#)

## Edges

An edge is a connection between two nodes. For example, a User node can have photos connected to it, and a Photo node can have comments connected to it. The following cURL example will return a list of photos a person has published to Facebook.

```
curl -i -X GET \
  "https://graph.facebook.com/USER-ID/photos?access_token=ACCESS-TOKEN"
```

Each ID returned represents a Photo node and when it was uploaded to Facebook.

```
    {
  "data": [
    {
      "created_time": "2017-06-06T18:04:10+0000",
      "id": "1353272134728652"
    },
    {
      "created_time": "2017-06-06T18:01:13+0000",
      "id": "1353269908062208"
    }
  ],
}
```

[](https://developers.facebook.com/docs/graph-api/overview#)

## Fields

Fields are node properties. When you query a node, or an edge, it returns a set of fields by default, as the examples above show. However, you can specify which fields you want returned by using the `fields` parameter and listing each field. This overrides the defaults and returns only the fields you specify, and the ID of the object, which is always returned.

The following cURL request includes the `fields` parameter and the User's name, email, and profile picture.

```
curl -i -X GET \
  "https://graph.facebook.com/USER-ID?fields=id,name,email,picture&access_token=ACCESS-TOKEN"
```

#### Data Returned

```
{
  "id": "USER-ID",
  "name": "EXAMPLE NAME",
  "email": "EXAMPLE@EMAIL.COM",
  "picture": {
    "data": {
      "height": 50,
      "is_silhouette": false,
      "url": "URL-FOR-USER-PROFILE-PICTURE",
      "width": 50
    }
  }
}
```

### Complex Parameters

Most parameter types are straightforward primitives such as `bool`, `string` and `int`, but there are also `list` and `object` types that can be specified in the request.

The `list` type is specified in JSON syntax, for example: `["firstitem", "seconditem", "thirditem"]`

The `object` type is also specified in JSON syntax, for example: `{"firstkey": "firstvalue", "secondKey": 123}`
Nguồn:: [Overview - Graph API](https://developers.facebook.com/docs/graph-api/overview)
