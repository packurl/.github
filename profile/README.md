# What is packurl?

**Packurl** lets you embed data inside a long https url (web address).

Once the link is opened, the content is extracted locally in the browser, and never sent anywhere.

It's like a zip archiver, except that you have a url instead of a zip file, and you only need a browser to create the archive or extract it.

#

**Packurl** software is devided into two parts, and hosted on two different domains.

The apex domain (`http://packurl.net`) is for the long https urls themselves and the [service worker](https://web.dev/learn/pwa/service-workers/) that the browser uses to decrypt and decompress the content. The user data is stored in the hash part of the url (after the `#`) and never sent to the server behind that domain. The server implementation even makes sure that the data is not read even if the `#` is omitted by mistake, by interrupting the connection early if that is the case. The only things behind this urls are the service worker implementation, and the manifests and installation pages required to have that service worker installed properly.

The www domain (`http://www.packurl.net`) is where the user can generate those urls easily through the use of pre-made templates. It hosts the web application and the implementation of all the templates. Unlike the apex domain, the www domain is behind a [CDN](https://developer.mozilla.org/en-US/docs/Glossary/CDN) ([Cloudflare](https://www.cloudflare.com/cdn/)).
