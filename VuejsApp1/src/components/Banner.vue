<script setup>
    import { ref } from 'vue'
</script>

<template>
    <div class="banner-container">
        <div class="banner-item">
            {{ title }}
            <div class="social-container">
                <a href="https://github.com/DeetonRushy">
                    <img class="small-image" src="../assets/github.png" />
                </a>
            </div>
        </div>
        <div class="social-container">
        </div>
        <p>
            This is my first ever experience with Vue. Safe to say that I enjoy it.
        </p>
    </div>
</template>

<script>
export default {
  name: 'Banner',
  props: {
      title: String,
      socials: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .banner-container {
        box-sizing:content-box;
        flex: 1 0 250px;
        margin: 1rem;
        padding: 1rem;
        /*border: 1px solid #000; */
        border-radius: 5px;
        background-color: inherit;
        font-family: 'Cascadia Code';
        color: white;
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
        background-color: cornflowerblue;
        font-family: 'Cascadia Code';
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
    }
</style>