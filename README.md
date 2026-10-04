# pit stop school.

A 3D walkthrough for kids. Change a tire and change the oil on a 1975 Porsche 911 Turbo, right from a phone or laptop.
Built for Cars & Black Coffee, Sparkhouse x paidnfull, Saturday 10.24, 500 N. Tryon St, Charlotte.

## Run it

It is one static page. It only needs a local web server because browsers block loading the 3D model from a plain file:// URL.

    cd pit-stop-school
    python3 -m http.server 8080

Then open http://localhost:8080 in a browser. Or use `npx serve .` if you prefer Node.

To put it on a phone at the event, run the server on a laptop and open http://<laptop ip>:8080 from the phone on the same wifi.
Everything is bundled, including the 3D library, the fonts and the model, so it works with no internet.

## Deploy it

Drop the whole folder on any static host (Vercel, Netlify, GitHub Pages, Cloudflare Pages). No build step.

## What is in here

    index.html            the whole app: markup, styles, lessons and the 3D scene
    model/porsche_930.json   the car, glTF with the binary embedded (see credit below)
    lib/                  three.js r147 and three loaders/controls (MIT)
    fonts/                Inter Tight and Geist Mono (OFL), via fontsource

## Edit the lessons

Everything a kid reads lives in one object in index.html, `const lessons = { tire: {...}, oil: {...} }`.
Each step has a `title`, `text`, an optional `note` (the gold callout), optional `tools` chips, a `cam` preset and an optional `task` the kid has to tap through.
The quick check questions sit in each lesson's `quiz` array.

## Credits

3D model: "Porsche 911 (930) Turbo 1975" by Lexyc16, CC BY 4.0. https://sketchfab.com/3d-models/porsche-911-930-turbo-1975-de1ffd344c41481892511f7fd332c136
Keep that credit anywhere this is shown. The car's design is Porsche AG's.
