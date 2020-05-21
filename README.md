spotify-backup-playlist
=======================

A Python 3 script that exports all Spotify playlists for a logged-in user.

To run the script, [save it from here](https://raw.githubusercontent.com/bitsofpancake/spotify-backup/master/spotify-backup.py) and double-click it. It'll ask you for a filename and then pop open a web page so you can authorize access to the Spotify API. Then the script will load your playlists and save a tab-separated file with your playlists that you can open in Excel. You can even copy-paste the rows from Excel into a Spotify playlist.

First, ensure you're running Python 3:

	python -V

If not, [update](https://formulae.brew.sh/formula/python#default) `python` with `brew`. (Also handy: [create aliases](https://opensource.com/article/19/5/python-3-default-mac) for `python3`.)

Run the script from the command line to get all playlists:

	python spotify-backup.py playlists.txt

Adding `--format=json` will give you a JSON dump with everything that the script gets from the Spotify API. If for some reason the browser-based authorization flow doesn't work, you can also [generate an OAuth token](https://developer.spotify.com/web-api/console/get-playlists/) on the developer site (with the `playlist-read-private` permission) and pass it with the `--token` option.

Collaborative playlists and playlist folders don't show up in the API, sadly.

The `python spotify-backup.py` command will also output a playlist `id`. Pass this `id` value as an argument for `spotify-backup-playlists.py`, like so:

	python spotify-backup-playlists {id}

Where `{id}` is the `id` of the playlist you'd like to back up (returned in the `python spotify-backup.py` command).

Happy backups.