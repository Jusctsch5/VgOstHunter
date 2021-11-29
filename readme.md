# VgOstHunter
Aids in processing of videogame ost playlists on sites such as youtube. Processing is described as review and download of interested musical pieces in a playlist. Should only be run on videos that you have the rights to, as any software that uses youtube-dl should be used for.

# Workflow: Main Use Case (download mp3s for game)
Input:  List of Game Names, Configuration (destination directory, interactive bool, auto download outliers bool, search match level of confidence)
Output: Names of selected/downloaded mp3s

- For each game in list of game names: Performs youtube search on 'game name', looking for playlists
  - Grab the playlist with the highest match => than the provided "level of confidence", and/or most views 
  - Display metadata for the playlist: Name of playlist, Number of songs in playlist, Total views of playlist
  - Display metadata for each song in playlist: Name of song, Total views
  - If interactive bool is set, play the song and wait for either y/n. y- ultimately download file, n- don't download file.
      - Move to the next song in the playlist, continue
  - If interactive bool is not set, run 'identify outliers' algorithm e.g., grab the 'n' videos with the most views 
  - Either case results in a list of videos to download. 
  - Download list of videos using youtube-dl, highest quality mp3, into configured destination directory
- Continue for each game in list
