<template>
  <div class="headrItem">
    <h2>My Vue App</h2>
    <div id="nav">
      <router-link :to="{name: 'home'}">Home</router-link>
      <router-link :to="{name: 'about'}">About</router-link>
      <router-link :to="{name: 'contact'}">Contact</router-link>
      <router-link :to="{name: 'testimonial'}">Testimonial</router-link>
    </div>
  </div>  
</template>

<style>
.headrItem {
  position: fixed;
  width: 100%;
  background-color: #160b4d;
  color: #ffcf3c;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

#nav a {
  color: #ffcf3c;
  padding: 20px;
  text-decoration: none;
}

#nav a:hover {
  color: #8572b9;
}
</style>
