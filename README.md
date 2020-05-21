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

Limited to 50 playlists. Playlists limited to 100 tracks.

spotify-backup-playlist.py
---------------------------

This command lets you backup an individual playlist's tracks (by playlist ID).

The `python spotify-backup.py` command will also output a playlist `id`. Alternatively, in the Spotify desktop client (macOS, and I presume Windows also—not mobile) you can right-click a playlist in the left-hand sidebar list and select **Share > Copy Spotify URI**. This will output a string like so:

	spotify:playlist:AaBbCcDdEeFfGgHhIiJjKk

Wherein the value after `spotify:playlist:` is the playlist `id`.

Pass this `id` value as an argument for `spotify-backup-playlist.py`, like so:

	python spotify-backup-playlist {playlist_id}

Where `{playlist_id}` is the `id` of the playlist you'd like to back up.

This will output to a file as such:

	{playlist_id} - {playlist_name}.txt

Where `{playlist_id}` is the `id` and `{playlist_name}` is the name of the playlist.

Fields exported for each track are as follows:

+ `id`: track ID
+ `name`: track name
+ `artists`: track artists, separated by `, `
+ `album`: album name for this track
+ `added_at`: date this track was added to the playlist
+ `uri`: Spotify URI of track (playlist independent)
+ `url`: Spotify URL of track (playlist independent), sharable

Open a new file in Excel and choose **File > Import**, and select the outputted `.txt` file. (Be sure to specify the **File origin** as **Unicode (UTF-8)**.)

Happy backups.