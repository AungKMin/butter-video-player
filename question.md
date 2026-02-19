# Overview

---

Create a basic HTML5 video player that can track how much of a video has been watched.

# **System Description**

Produce a single page that plays an MP4 video using a basic HTML5 player and some custom controls. Your player should track the portions of the video that have been watched and rewatched.

---

- Implement and test your solution in the google chrome browser.
- This can all be accomplished with good old javascript, HTML, and CSS. Part of the exercise is picking the right tools for the task.
- [ ]  Include a README with your submission telling us the browser and OS you used, an explanation of your solution's performance characteristics, anything you learned or would do differently if doing this again, and any other notes you think are relevant.

# Requirements

---

## Playbar

---

- [ ]  Always show the current time of the video, next to the play head.
- [ ]  Clicking in the playbar should move the play head there, and seek the video accordingly.
- [ ]  The play head should be horizontally draggable and update the time of the video as it moves.

## Play / Pausing

---

- [ ]  Clicking the video while it’s playing pauses the video.
- [ ]  Clicking the video while it’s paused plays the video.

## Tracking Engagement

---

- [ ]  Log a message when 25% of the video has been rewatched
- A rewatch is when a section of the video is watched at least twice
    - Skipped sections don't count towards rewatches
    - Rewatched sections for the same time interval should not compound

Suppose a user watched a 60 second video.

Example 1: If the user seeks to second 5 and watches until second 30, they've rewatched 25 seconds, or 41.7% of the video.

Example 2: If the user watches seconds 5-10 and seconds 15-20, they've rewatched 10 seconds, or 16.7% of the video.

Example 3: If the user watches seconds 5-10 four different times, they've only reawatched 5 seconds.

- The solution should be accurate to at least 1 second of granularity.
- When performing calculations, you can assume the video can be anywhere from 1 second to 4 hours long, although the sample file below is 1 minute 46 seconds.
- Whatever solution you choose, please note its performance characteristics in your README.

# **Bonus!**

---

- Visual: Polish, make it look good! Make it fun to interact with
- Tracking: Do you have an idea of the time/space complexity of your approach?
- Modularity: how difficult is it to put more than one video on the same page?
- Reusability: how difficult is it to track a different rewatched percentage?
- Consistency: How would the player/tracker behave with videos of different lengths?

# References

---

You can use this file for your video

Please let us know if you need anything clarified or if you have any questions!

[web-demo.mp4](attachment:8afce748-c642-4036-b9ce-0bec8a47fb63:web-demo.mp4)