<template>
  <div class="home">
    <h1>Welcom to My Vue App</h1>
    <div class="container">
      <img id="home-img" :src="img">
      <div>
        <p>{{ firstPara }}</p>
        <p>{{ secondPara }}</p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      img: require("../assets/vue_bg.jpg"),
      firstPara: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam vehicula euismod aliquet. Aenean ac nisi eget turpis auctor semper eu non sapien. Maecenas a libero ac risus feugiat facilisis. Aenean fermentum, metus vitae aliquam consequat, felis diam iaculis sem, at mattis ex dolor eget diam. Nullam fermentum in neque eget volutpat. Integer rutrum eget dolor sed pharetra. Fusce lacinia ex quam, aliquet faucibus lorem ultricies eu.",
      secondPara:  "Mauris laoreet est congue ullamcorper ultrices. Nullam turpis risus, aliquet ut commodo sed, ultricies quis lorem. Suspendisse potenti. Suspendisse cursus blandit leo quis vulputate. Cras imperdiet quis lorem finibus placerat. Duis nunc mauris, interdum a leo non, rutrum fermentum tellus. In dignissim facilisis sem vitae luctus. Aliquam eleifend elementum tellus. Nullam vestibulum eu arcu eget suscipit."
    }
  }
}
</script>

<style>
  .home {
    max-width: 1000px;
    margin: auto;
    text-align: left;
    padding-top: 100px;
    padding-bottom: 70px;
  }
  
  .container {
    display: flex;
    align-items: center;
  }

  .container * {
    margin: 10px;
  }

  #home-img {
    width: 300px;
  }
</style>
