---
share: true
created: 2023-10-30T14:29
updated: 2024-06-30T20:46
---
```
          userinfo       host      port
          ┌──┴───┐ ┌──────┴──────┐ ┌┴─┐
  https://john.doe@www.example.com:1234/forum/questions/?tag=networking&order=newest#top
  └─┬─┘   └─────────────┬─────────────┘└───────┬───────┘ └────────────┬────────────┘ └┬┘
  scheme            authority                path                   query          fragment
          userinfo       host      port
          ┌──┴───┐ ┌──────┴──────┐ ┌┴─┐
  https://john.doe@www.example.com:1234/forum/questions/?tag=networking&order=newest#:~:text=whatever
  └─┬─┘   └─────────────┬─────────────┘└───────┬───────┘ └────────────┬────────────┘ └───────┬───────┘
  scheme            authority                path                   query                 fragment

  ldap://[2001:db8::7]/c=GB?objectClass?one
  └┬─┘   └─────┬─────┘└─┬─┘ └──────┬──────┘
  scheme   authority   path      query

  mailto:John.Doe@example.com
  └─┬──┘ └────┬─────────────┘
  scheme     path

  news:comp.infosystems.www.servers.unix
  └┬─┘ └─────────────┬─────────────────┘
  scheme            path

  tel:+1-816-555-1212
  └┬┘ └──────┬──────┘
  scheme    path

  telnet://192.0.2.16:80/
  └─┬──┘   └─────┬─────┘│
  scheme     authority  path

  urn:oasis:names:specification:docbook:dtd:xml:4.1.2
  └┬┘ └──────────────────────┬──────────────────────┘
  scheme                    path
```
Nguồn:: [Uniform Resource Identifier - Wikipedia](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)