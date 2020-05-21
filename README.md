spotify-backup-playlist
=======================

A set of Python 3 scripts that export Spotify playlist tracks for a logged-in user.

Setup
-----

First, ensure you're running Python 3:

	python -V

If not, [update](https://formulae.brew.sh/formula/python#default) `python` with `brew`. (Also handy: [create aliases](https://opensource.com/article/19/5/python-3-default-mac) for `python3`.)

spotify-backup.py
-----------------

Run the script from the command line to get all playlists:

	python spotify-backup.py playlists.txt

On first run, the script will open a web page in your browser asking you to authorize access to the Spotify API.

Adding `--format=json` will give you a JSON dump with everything that the script gets from the Spotify API. If for some reason the browser-based authorization flow doesn't work, you can also [generate an OAuth token](https://developer.spotify.com/web-api/console/get-playlists/) on the developer site (with the `playlist-read-private` permission) and pass it with the `--token` option.

Collaborative playlists and playlist folders don't show up in the API.

spotify-backup-playlists.py
---------------------------

The `python spotify-backup.py` command will also output a playlist `id`. Pass this `id` value as an argument for `spotify-backup-playlists.py`, like so:

	python spotify-backup-playlists {id}

Where `{id}` is the `id` of the playlist you'd like to back up (returned in the `python spotify-backup.py` command).

Happy backups.