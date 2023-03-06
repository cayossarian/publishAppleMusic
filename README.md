# publishAppleMusic

## Purpose
These shortcuts provide a means to copy from one Apple Music playlist to another without creating duplicates in the target playlist.  Two scripts work together, the first shortcut defines a Dictionary containing keys and values for toPlayList and fromPlayList.  The first script may contain more than one Dictionary and invoke the worker script repeatedly.

This functionality provides a means to automate the publishing of "Smart Playlists" by specifying songs from the source Smart Playlist and placing those songs in an existing regular playlist that is part of a user's music profile (published by Music and followed by other users).  

You can test this automation by manually creating two playlists, A and B (put one or more songs in playlist A) and running the shortcut "Test A to B."  You can run this shortcut repeatedly and only new songs that don't exist in playlist B will be copied to B without duplicates.

## Method to automate Smart Playlists
1. Create one or more Smart Playlists that you wish to publish (these will be defined as "fromPlayList" in the first Shortcut Dictionary)
2. Create corresponding regular playlist(s) and publish them in your edit setting in your Music user profile (https://support.apple.com/guide/music/share-music-with-friends-mus140a2e93/mac).  These publicly shared playlists should be defined as "toPlayList" in the first shortcut's Dictionary.
3. Create or copy the existing A-B test shortcut to pass one or more Dictionaries containing keys for "fromPlayList" and "toPlayList"
4. Test the driver script (e.g., Test A to B shortcut) at least once by executing it and give it permission to invoke the worker script (asks only once)
5. Set up a personal automation (in the Shortcuts app) on an iPhone or iPad that invokes the Dictionary script to run at some predetermined time and interval.  Allow the personal workflow to run when the device is locked.  It's optional to have this workflow notify the user that it has run.

## Performance
Because there is no native Apple means to merge one playlist into another without duplicates, the script must look at every song in the source and try to match with a same song in the target playlist.  If the target is empty, the copy is quick.  If the source contains many entries the script takes considerably longer.  For example when the source has over a thousand songs and target is similarly populated, the script could take a minute or more depending on the speed of the device.  Since one is presumably running these on a schedule during off hours, performance should not be an issue.
