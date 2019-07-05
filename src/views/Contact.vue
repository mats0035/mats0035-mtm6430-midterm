<template>
  <div class="contact">
    <h1>Contact</h1>
    <div class="contact-container">
      <div>
        <h3>Address</h3>
        <p>{{ address1 }}<br>{{ address2 }}<br>{{ phone }}</p>
      </div>
      <div>
        <h3>Hours of operation</h3>
      <div class="hrsOperation">
        <ul>
          <li v-for="ops in hrsOps">{{ ops.day }}: {{ ops.hours }}</li>
        </ul>
      </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      address1: "1685 Woodroffe Avenue,",
      address2: "Ottawa, Ontario. K2G1V8",
      phone: "613-727423",
      hrsOps: [
        {day: "Monday", hours: "8AM - 6PM"},
        {day: "Tuesday", hours: "8AM - 6PM"},
        {day: "Wednesday", hours: "8AM - 6PM"},
        {day: "Thursday", hours: "8AM - 6PM"},
        {day: "Friday", hours: "8AM - 5PM"},
        {day: "Saturday", hours: "10AM - 4PM"},
        {day: "Sunday", hours: "10AM - 2PM"}
      ]
    }
  }
}
</script>

<style>
  .contact {
    max-width: 800px;
    margin: auto;
    text-align: left;
    padding-top: 100px;
  }

  .contact-container {
    display: flex;
    justify-content: space-evenly;
    align-items: baseline;
  }

  h3 {
    text-decoration: underline;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  .hrsOperation {
    display: felx;
    justify-content: center;
  }
</style>
