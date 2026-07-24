---
share: true
created: 2023-10-30T14:29
updated: 2026-07-06T21:40
---
[quacau.fibery.io/api/graphql/space/Định\_kỳ\_đóng\_phí](https://quacau.fibery.io/api/graphql/space/Định_kỳ_đóng_phí):
```graphql
query {
  findArticles(published: {is: true} orderBy: {creationDate: DESC}) {
    name
    publicId
    content {
      md
    }
    creationDate
    date
    description {
      text
    }
    seoTitle
    seoDescription {
      text
    }
    slug
    files {
      secret
      name
      contentType
    }
  }
}
```
Nguồn:: 
