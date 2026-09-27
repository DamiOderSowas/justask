# Just Ask

A tiny website inspired by the idea behind projects like nohello and dontasktoask.

The goal is simple:

Don't send only "Hello" and wait.

Don't ask if you can ask a question.

Just send your question directly.

## Features

- German and English
- Automatic language selection
- IP based country detection
- German for Germany, Austria, Switzerland and Liechtenstein
- English for most other countries
- Browser language fallback
- Manual DE / EN language switch
- User language preference stored in `localStorage`
- Responsive design
- No framework
- No build step
- No npm dependencies
- Simple HTML, CSS and JavaScript
- Copy buttons for example messages

## Project structure

```text
.
├── index.html
└── README.md
```

## Run locally

No installation is required.

You can simply open:

```text
index.html
```

in your browser.

For a proper local web server, you can also use Python:

```bash
python3 -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

## Language detection

The website checks the language in this order:

1. Previously selected language from `localStorage`
2. Country detection by IP
3. Browser language
4. English as the default fallback

German is automatically selected for:

```text
DE
AT
CH
LI
```

All other countries use English by default.

## IP detection

The current implementation uses:

```text
https://ipapi.co/country/
```

This is only intended as a simple solution for a small static website.

For production deployments behind Cloudflare, it is better to use Cloudflare's country information instead of requesting an external Geo-IP service.

## Hosting

Because the project is fully static, it can be hosted almost anywhere.

Examples:

- Cloudflare Pages
- GitHub Pages
- Nginx
- Apache
- Netlify
- Vercel
- Any basic web server

## Nginx example

Example configuration:

```nginx
server {
    listen 80;
    server_name example.com www.example.com;

    root /var/www/justask;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

For a public website, HTTPS should also be enabled.

## Customization

Most settings are directly inside `index.html`.

You can easily change:

- Website name
- Text
- Examples
- Colors
- Supported languages
- Country mappings
- Footer
- Metadata

To add another German speaking country to automatic detection, edit:

```js
const germanCountries = [
  "DE",
  "AT",
  "CH",
  "LI"
];
```

## Privacy

The basic website itself does not require:

- Accounts
- Cookies
- Analytics
- Tracking
- A database

The current IP country detection sends a request to an external Geo-IP provider.

If you want to minimize third party requests, replace this mechanism with server side or Cloudflare based country detection.

## Philosophy

Chat does not need to work like this:

```text
Alex: Hello

Sam: Hi

Alex: Can I ask you something?

Sam: Sure

Alex: My server is returning a 502 error. Do you know why?
```

It can simply be:

```text
Alex: Hey, my server is returning a 502 error after the last deployment.
Do you know what might be causing it?
```

Friendly communication can still be direct communication.

## License

Choose a license that fits how you want the project to be used.

If you want the project to remain open source, common options include:

- MIT
- Apache-2.0
- GPL-3.0

If you do not want others to freely copy, redistribute or commercially reuse the project, do not use an open source license and add your own copyright notice instead.

Example:

```text
Copyright © 2026. All rights reserved.

Unauthorized copying, modification, distribution or commercial use of this
project is prohibited without prior written permission.
```
