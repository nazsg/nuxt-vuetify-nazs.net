<template>
  <div>
    <!-- The video -->
    <video autoplay muted loop id="myVideo">
      <source src="/Jupiter.mp4" type="video/mp4" />
    </video>

    <!-- Optional: some overlay text to describe the video -->
    <div class="content">
      <!-- <h1>Heading</h1> -->
      <p>i know... you're welcome</p>
      <nuxt-link to="/">Home</nuxt-link>
      <!-- Use a button to pause/play the video with JavaScript -->
      <button id="myBtn" @click="pause">Pause</button>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'video',
  methods: {
    pause() {
      let video = document.getElementById('myVideo')

      // Get the button
      let btn = document.getElementById('myBtn')

      // Pause and play the video, and change the button text
      // function myFunction() {
      if (video.paused) {
        video.play()
        btn.innerHTML = 'Pause'
      } else {
        video.pause()
        btn.innerHTML = 'Play'
      }
      // }
    },
  },
}
</script>

<style>
/* Style the video: 100% width and height to cover the entire window */
#myVideo {
  position: fixed;
  right: 0;
  bottom: 0;
  min-width: 90%;
  min-height: 90%;
}

/* Add some content at the bottom of the video/page */
.content {
  position: fixed;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  color: #f1f1f1;
  width: 100%;
  padding: 20px;
}

/* Style the button used to pause/play the video */
#myBtn {
  width: 200px;
  font-size: 18px;
  padding: 10px;
  border: none;
  background: #000;
  color: #fff;
  cursor: pointer;
}

#myBtn:hover {
  background: #ddd;
  color: black;
}
</style>
