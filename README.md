# style-transfer-contest

This repo contains the archived results of Cloudinary’s Style Transfer Contest, held in 2017.

The archive was created by executing the following command:

`wget -prkEH -Dres.cloudinary.com https://faas-cloudinary.com/wt-60a287cd40c53f6e56bd60ac8922bc3e-0/style-transfer/view/no-token`

Here’s a breakdown of those gnarly `wget` switches:

- `-p` downloads resources (like images) necessary to render the page (and not just the HTML)
- `-r` follows links recursively (default depth level 5)
- `-k` converts absolute URLs (starting with http://) to local, relative URLs ( starting with ./ or ../../../ or whatever)
- `-E` renames files so their extension matches their type (e.g., .asp → .html)
- `-H` spans hosts (so res.cloudinary images get downloaded)
- `-D[hostname]` limits `-H` so that only links/resources on that host gets followed/downloaded (can specify multiple with commas, like `-Dres.cloudinary.com,demo-res.cloudinary.com`) (edited)

