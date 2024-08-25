---
share: true
created: 2023-10-30T14:29
updated: 2024-08-21T23:57
---
### About the Google Analytics client

First, you need to set up a client in the server container. A client is a Tag Manager resource type that intercepts certain types of incoming HTTP requests and generates **events** that are passed to a destination, like Google Analytics 4.

In this case, the HTTP request is a **Google Analytics 4** event, so you need to configure the built-in **Google Analytics: GA4** client. You only need one GA4 client.

  
  
![Diagram showing how the GA4 client serves as a library and a proxy for GA4 events.](https://developers.google.com/static/tag-platform/learn/images/analytics-client.png)

The GA4 client has a dual purpose.

1. It serves as a proxy for Google Analytics 4 library that loads in the browser. GA4, just like any other analytics service running in the browser, requires a JavaScript library to work. Instead of the browser loading this library directly from Google's content distribution network, you can configure the GA4 client to allow the library to be loaded through your server container instead.
2. The client also serves as a proxy for the GA4 event requests themselves. Instead of the browser sending the events directly to Google's analytics servers, they are first sent to the server container, where the GA4 client intercepts them and dispatches them onward to Google servers (and any other destinations you like).

## Setting up the GA4 client

To set up the GA4 client in the server, follow the next four steps.

### 1. Configure the client

To configure the GA4 client:

1. In your server container, open **Clients**.
2. Click on the **GA4 client** to open its configuration.
3. Set up your GA4 client with the following parameters. Save when you are done.

![Screenshot of the tag configuration dialog](https://developers.google.com/static/tag-platform/learn/images/client-configuration.png)
Nguồn:: [Configuring the Google Analytics 4 data stream with server-side tagging  |  Server-side tagging fundamentals  |  Google for Developers](https://developers.google.com/tag-platform/learn/sst-fundamentals/5-sst-setup-analytics)