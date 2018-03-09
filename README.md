# style-transfer-contest

This repo contains the archived results of Cloudinary’s Style Transfer Contest, held in Sept 27th – October 4th, 2017.

The archive was created by executing the following command:

`wget -prHkE --level=1 -Dres.cloudinary.com,faas-cloudinary.com,codepen.io,cloudinary-res.cloudinary.com,code.jquery.com,cdnjs.cloudflare.com https://faas-cloudinary.com/wt-60a287cd40c53f6e56bd60ac8922bc3e-0/style-transfer/view/no-token`

And then doing a couple of additional things, manually. More on the manual steps later. First, Here’s a breakdown of those gnarly `wget` switches:

- `-p` downloads resources (like images) necessary to render the page (and not just the HTML)
- `-r` follows links recursively (default depth level 5)
- `--level 1` sets the depth level to 1
- `-k` converts absolute URLs (starting with http://) to local, relative URLs ( starting with ./ or ../../../ or whatever)
- `-E` renames files so their extension matches their type (e.g., .asp → .html)
- `-H` spans hosts (so res.cloudinary images get downloaded)
- `-D[hostname]` limits `-H` so that only links/resources on that host gets followed/downloaded (can specify multiple with commas, like `-Dres.cloudinary.com,demo-res.cloudinary.com`)

External hosts that were not included in the `wget -D` list, and why:

- `fonts.googleapis.com`, because it might break the terms of service (?) and it seems Google serves different things to different browsers depending on UA string and I didn't want to get into the business of figuring out how or why they do that or how I should or shouldn’t spoof with yet more `wget` options.
- `platform-api.sharethis.com`, because when I did this I got CORS errors. Without it, I still get CORS errors, but ¯\_(ツ)_/¯
- `cloudinary.com`, because while I do want a stylesheet from over there I did not want to download the linked-to cloudinary.com homepage.

In order to get that stylesheet, I: 

1. Manually downloaded `https://cloudinary.com/stylesheets/g/cloudinary_public.css?1500989656` and saved it to this repo at `[repo root]/cloudinary.com/stylesheets/g/cloudinary_public.css`.
2. Found `https://cloudinary.com/stylesheets/g/cloudinary_public.css?1500989656` + replaced with `../../../../cloudinary.com/stylesheets/g/cloudinary_public.css` on every file in `/faas-cloudinary.com/wt-60a287cd40c53f6e56bd60ac8922bc3e-0/style-transfer/view/`

One more manual thing. Because I did not want the canonical URL for this archive to be:

`https://cloudinary-developers.github.io/style-transfer-contest/faas-cloudinary.com/wt-60a287cd40c53f6e56bd60ac8922bc3e-0/style-transfer/view/no-token?view=leader&vote=.html`

(🤮)

I copied `/wt-60a287cd40c53f6e56bd60ac8922bc3e-0/style-transfer/view/no-token?view=leader&vote=.html` to `/index.html` and did a couple of find/replaces on it to make sure that its links still worked.

**Find**: `../../../../`
**Replace**: `./`

(makes the cross-domain links work)

**Find**: `no-token`
**Replace**: `./faas-cloudinary.com/wt-60a287cd40c53f6e56bd60ac8922bc3e-0/style-transfer/view/no-token`

(makes the same-domain links to the other views work)

So now this archive is accessible at [https://cloudinary-developers.github.io/style-transfer-contest/](https://cloudinary-developers.github.io/style-transfer-contest/), and all of the links work.

🎉 *fin* 🎉