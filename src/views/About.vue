<template>
  <div class="about">
    <h1>About the Vue App</h1>
    <div class="about-container">
      <img :src="firstImg">
      <p>{{ firstPara }}</p>
    </div>
    <div class="about-container">
      <p>{{ secondPara }}</p>
      <img :src="secondImg">
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      firstImg: require("../assets/logo.png"),
      secondImg: require("../assets/logo.png"),
      firstPara: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam vehicula euismod aliquet. Aenean ac nisi eget turpis auctor semper eu non sapien. Maecenas a libero ac risus feugiat facilisis. Aenean fermentum, metus vitae aliquam consequat, felis diam iaculis sem, at mattis ex dolor eget diam. Nullam fermentum in neque eget volutpat. Integer rutrum eget dolor sed pharetra. Fusce lacinia ex quam, aliquet faucibus lorem ultricies eu.",
      secondPara:  "Mauris laoreet est congue ullamcorper ultrices. Nullam turpis risus, aliquet ut commodo sed, ultricies quis lorem. Suspendisse potenti. Suspendisse cursus blandit leo quis vulputate. Cras imperdiet quis lorem finibus placerat. Duis nunc mauris, interdum a leo non, rutrum fermentum tellus. In dignissim facilisis sem vitae luctus. Aliquam eleifend elementum tellus. Nullam vestibulum eu arcu eget suscipit."
    }
  }
}
</script>

<style>
  .about {
    max-width: 800px;
    margin: auto;
    text-align: left;
    padding-top: 100px;
    padding-bottom: 70px;
  }

  .about-container {
    display: flex;
    justify-content: center;
    align-items: center;

  }

  .about-container * {
    margin: 10px;
  }
</style>
