<script setup>
const props = defineProps({
  socials: {
    type: Array,
    default: []
  },
  title: {
    type: String,
    default: 'Banner'
  }
})
</script>

<template>
    <div class="banner-container">
        <div class="banner-item">
            {{ title }}

          <div class="social-container">
            <a href="https://github.com/DeetonRushy">
              <img class="small-image" src="../assets/github.png"  alt="Github"/>
            </a>
          </div>
        </div>
        <div class="social-container">
        </div>
        <p class="rainbow">
            This is my first ever experience with Vue. Safe to say that I enjoy it.
        </p>
    </div>
</template>

<script>
export default {
  name: 'Banner'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .banner-container {
      box-sizing: content-box;
      flex: 1 0 250px;
      margin: 1rem;
      padding: 1rem;
      /*border: 1px solid #000; */
      border-radius: 5px;
      background-color: inherit;
      font-family: 'Cascadia Code',ui-monospace;
      color: black;
      font-size: 1.5rem;
      font-weight: bold;
    }

    .banner-item {
        display: flex;

        box-sizing: content-box;
        flex: 1 0 250px;
        margin: 1rem;
        padding: 1rem;
        border: 1px solid #000;
        border-radius: 5px;
        background-color: #4a4949;
        font-family: 'Cascadia Code', ui-monospace;
        color: white;
        font-size: 1.5rem;
        font-weight: bold;
    }

    .social-container{
        margin-left: auto;
        margin-right: 0;
    }

    .small-image {
        width: 2em;
        height: 2em;
        border-radius: 50%;
    }

    .rainbow {
      background: linear-gradient(to right, red, green, blue, yellow, purple);
      -webkit-background-clip: text;
      color: transparent;
      animation: rainbow_animation 6s ease-in-out infinite;
      background-size: 400% 100%;
    }

    @keyframes rainbow_animation {
      0%,100% {
        background-position: 0 0;
      }

      50% {
        background-position: 100% 0;
      }
    }

</style>