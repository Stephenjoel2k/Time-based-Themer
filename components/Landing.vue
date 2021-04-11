<template>
  <div class="container" :class="theme">
    <div class="header">
      <h4 class="header-appname">musichabits.me</h4>
      <div class="header-image">
        <img v-if="theme === 'morning'" src="../static/png/morning.png" height="150px" alt="Morning">
        <img v-if="theme === 'afternoon'" src="../static/png/afternoon.png" height="150px" alt="Afternoon">
        <img v-if="theme === 'evening'" src="../static/png/evening.png" height="150px" alt="Evening">
      </div>
      <div class="header-text">
        <h4 class="greeting">good {{theme}},</h4>
        <h2 class="name">Stephen Joel</h2>
      </div>
    </div>
    <div class="body">
      <div class="buttons">
          <vs-button color="warning" type="border" @click="theme = 'morning'">
            <i class='bx bx-sun bx-md bx-burst-hover'></i>
          </vs-button>
          <vs-button color="primary" type="border" @click="theme = 'afternoon'">
            <i class='bx bx-brightness-half bx-md bx-burst-hover'></i>
          </vs-button>
          <vs-button color="primary" type="border" @click="theme = 'evening'">
            <i class='bx bxs-sun bx-md bx-burst-hover'></i>
          </vs-button>
          <vs-button color="primary" type="border" @click="theme = 'night'">
            <i class='bx bxs-moon bx-md bx-burst-hover'></i>
          </vs-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      theme: 'morning'
    }
  }
}
</script>

<style scoped>

  @import url('https://fonts.googleapis.com/css2?family=Work+Sans:wght@500&display=swap');

  .container{
    margin: auto;
    height: 100vh;
    background-color: var(--bg);
  }

  .header{
    height: 40vh;
    min-height: 350px;
    color: var(--color);
    background-color: var(--bg-header);
    border-radius: 0 0 80px 80px;
  }

  .header-appname{
    font-family: 'Work Sans', sans-serif;
    font-size: 15px;
    padding-left: 10%;
    padding-top: 15px;
  }

  .header-image{
    position: absolute;
  }

  .morning .header-image{
    right: 25px;
    top: 75px;
  }

  .afternoon .header-image{
    text-align: center;
    left: 0;
    right: 0;
    top: 50px;
  }

  .evening .header-image{
    left: 25px;
    top: 75px;
  }

  .header-text{
    position: relative;
    top: 200px;
    padding: 0 10%;
    text-transform: capitalize;
    font-family: 'Work Sans', sans-serif;
  }

  .header .greeting{
    font-size: 1rem;

  }

  .header .name{
    font-size: 2rem;
  }

  .afternoon .header-text{
    text-align: center;
  }

  .evening .header-text{
    text-align: right;
  }

</style>
