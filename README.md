# TatarJR Beats

Static bilingual site for TatarJR, a beatmaker and producer in Wroclaw.
Plain HTML, CSS and JavaScript. No build step, no dependencies, no framework.

Live at **https://mariamraouf.github.io/tatarjr-beats/**

## What is in here

    index.html          Polish version, this is the homepage
    en/index.html       English version
    assets/audio/       nine 45 second previews, mp3
    assets/img/         reel thumbnails, studio photo, logo, favicon, share image
    assets/video/       clip.mp4 hero background, clip2.mp4 the room section
    robots.txt          points crawlers at the sitemap
    sitemap.xml         both language versions, with hreflang
    .nojekyll           stops GitHub Pages running the files through Jekyll

## How it works

Both pages are the same page built twice, one per language. Every visible string
is pre written into the HTML so crawlers read real Polish and real English rather
than waiting on JavaScript. The PL and EN pages point at each other with hreflang,
and each one declares its own canonical. The language button at the top is a plain
link between the two.

Beats, prices and licence terms live in a `BEATS` array and a `PRICES` object near
the bottom of each file. The player, the crate and the waveforms all read from
those, so changing a price or adding a beat means editing the data, not the markup.

Structured data is a JSON-LD graph in the head: WebSite, WebPage, Person, and an
ItemList of all nine beats as Products with MP3 lease and Exclusive offers.

## Changing something

Edit both `index.html` and `en/index.html`, they are independent files.
Commit and push. GitHub Pages redeploys in about a minute.

To add a beat: drop the 45 second mp3 into `assets/audio/`, add an entry to the
`BEATS` array in both files, and add it to the `itemListElement` block in the
JSON-LD so it stays in sync.

## Moving to a real domain

Right now every canonical, hreflang and sitemap URL says
`https://mariamraouf.github.io/tatarjr-beats`. When a domain is bought:

1. Find and replace that string with the new domain in `index.html`,
   `en/index.html` and `sitemap.xml`.
2. Add a file called `CNAME` at the root containing just the domain.
3. Point the DNS at GitHub Pages, then set the custom domain in
   Settings, Pages on this repo.

Worth doing. A `.pl` domain helps in Polish results and a `.com` travels better.
Also note that `robots.txt` on a project page like this one is not actually read
by crawlers, they only read it at the domain root. On a custom domain it works.

## After it is live

1. Google Search Console, add the property, verify, submit `sitemap.xml`.
2. Put the link in the Instagram and TikTok bios. Those are the real traffic.
3. Bing Webmaster Tools takes the same sitemap, takes two minutes, worth it.
