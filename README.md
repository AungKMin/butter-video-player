# Local testing
1. Run `python3 -m http.server 8000` in this directory.
2. Go to `localhost:8000`
* Note: Since I'm only serving a html file and a mp4 file, I thought anything more is overkill.

# Time taken for transparency
10:20 am to 12:00 pm
1:30 pm to 2:20 pm
4:30 pm to 7:15 pm

# Performance Characteristics
* At every `timeupdate` event, the player updates some number of indices in `watchCounts` and `updatedLast`. Since `timeupdate` runs frequently (two runs likely fit in a time slice) and because I gate code execution in `timeupdate` with `if (video.seeking)`, this should be O(1).
* At every `seeked` event, the playe fills the entire `updatedLast` array with `false`, which is linear time complexity with the number of time slices in the video. This could be slow if the video is long. However, if the user doesn't seek in the video much, this performance hit shouldn't be very noticable. 
    * One approach to make the user experience smoother is to have two arrays. Keep one working "current" array. Keep another array filled with `false` values. When the user seeks, swap the pointers so that the current the current array becomes the one with `false` values. Asynchronously fill the "dirty", previously "current" array with `false` values. This makes the seek function run faster.

# Edge conditions
* If a user seeks to the same time slice as the last slice, we still count it as rewatching that slice even if the entire slice wasn't played. For example, assume a slice is 1 second. If a user seeks to the 0.5-second mark, we count that as replaying the entire slice.

# Bonus
## Visual: Polish, make it look good! Make it fun to interact with
* I added an engagement bar.
## Tracking: Do you have an idea of the time/space complexity of your approach?
* O(1) for the `timeupdate` event
* O(n) where n is the number of timeslices in the video for the `seeked` event
## Modularity: how difficult is it to put more than one video on the same page?
* You can have an array of videos and duplicate all of the variables for each video. Then `addEventListener` for all of the videos, where the callback function can use the video index to access the corresponding variables.
## Reusability: how difficult is it to track a different rewatched percentage?
* Just update the `ENGAGEMENT_THRESHOLD` variable.
## Consistency: How would the player/tracker behave with videos of different lengths?
* The video player should behave in a similar way, except that the callback for `seeked` would take longer (since it is linear in the number of timeslices in the video). This might result in the engagement behavior being slower than