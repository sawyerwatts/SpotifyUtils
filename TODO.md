# TODO

## Feature: Automatically add new songs to playlists

1. Lookup target artists from utils' DB/etc
2. Per artist, check for new songs
    - since last run?
    - [API doc to get artist's albums](https://developer.spotify.com/documentation/web-api/reference/get-an-artists-albums)
        - what if they do a partially released album?
        - also this seems to have poor precision
    - [API doc to get an album's tracks](https://developer.spotify.com/documentation/web-api/reference/get-an-album)
3. Add new songs to target playlists
    - [API doc to add a track to a playlist](https://developer.spotify.com/documentation/web-api/reference/add-items-to-playlist)
    - Is the `POST` atomic?
    - I don't think this is idempotent since `POST` but double check. Otherwise, will need to have
      uniq logic (if artists share an album, if `POST` fails on network resp, etc)
        - Make sure this doesn't collide w/ users removing a song manually!
4. Notify of new songs added
   - include link to playlist at new song's starting position?

- Prob want to have a tracker in the DB for what albums/songs have been added, and a state for
  {uploading | uploaded} so failures can be checked
