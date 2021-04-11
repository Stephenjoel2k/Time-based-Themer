<template>
  <div class="container" :class="theme">
    <div class="header" :class="visibility">
      <h4 class="header-appname">
        musichabits.me
      </h4>
      <div class="header-image">
        <img v-if="theme === 'morning'" src="../static/png/morning.png" height="150px" alt="Morning">
        <img v-if="theme === 'afternoon'" src="../static/png/afternoon.png" height="150px" alt="Afternoon">
        <img v-if="theme === 'evening'" src="../static/png/evening.png" height="150px" alt="Evening">
        <img v-if="theme === 'night'" src="../static/png/night.png" height="150px" alt="Night">
      </div>
      <div class="header-text">
        <h4 class="greeting">
          good {{ theme }}
        </h4>
        <h2 class="name">
          Riley Germany
        </h2>
      </div>
    </div>
    <div class="body">
      <div class="buttons">
        <vs-button @click="theme = 'morning'">
          <i class="bx bx-sun bx-md bx-burst-hover" />
        </vs-button>
        <vs-button @click="theme = 'afternoon'">
          <i class="bx bx-brightness-half bx-md bx-burst-hover" />
        </vs-button>
        <vs-button @click="theme = 'evening'">
          <i class="bx bxs-sun bx-md bx-burst-hover" />
        </vs-button>
        <vs-button @click="theme = 'night'">
          <i class="bx bxs-moon bx-md bx-burst-hover" />
        </vs-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      theme: 'morning',
      visibility: 'full'
    }
  },
  mounted () {
    const date = new Date()
    const hour = date.getHours()
    if (hour >= 4 && hour < 12) {
      this.theme = 'morning'
    } else if (hour >= 12 && hour < 17) {
      this.theme = 'afternoon'
    } else if (hour >= 17 && hour < 22) {
      this.theme = 'evening'
    } else {
      this.theme = 'night'
    }
  },
  beforeMount () {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.handleScroll)
  },
  methods: {
    handleScroll () {
      if (window.scrollY < 50) {
        this.visibility = 'full'
      } else if (window.scrollY >= 50 && window.scrollY < 300) {
        this.visibility = 'partial'
      } else {
        this.visibility = 'none'
      }
    }
  }
}
</script>

<style scoped>

  @import url('https://fonts.googleapis.com/css2?family=Work+Sans:wght@500&display=swap');

  /** Container */

  .container{
    margin: auto;
    height: 500vh;
    background-color: var(--bg);
    overflow-x: hidden;
  }

  /** Header */

  .header{
    width: 100vw;
    position: fixed;
    color: var(--color);
    background-color: var(--bg-header);
    z-index: 999;
  }

  .header-appname{
    font-family: 'Work Sans', sans-serif;
    font-size: 15px;
    padding-left: 10%;
    padding-top: 1vh;
  }

  .header-image{
    position: absolute;
    animation: mover 2s alternate infinite;
  }

  /** Header with Full height */

  .full{
    height: 40vh;
    min-height: 325px;
    border-radius: 0 0 80px 80px;
  }

  .morning .full .header-image{
    right: 10vw;
    top: 10vh;
  }

  .afternoon .full .header-image{
    text-align: center;
    left: 0;
    right: 0;
    top: 7vh;
  }

  .evening .full .header-image, .night .full .header-image{
    left: 10vw;
    top: 10vh;
  }

  /** Header with partial height */

  .partial {
    height: 25vh;
    border-radius: 0 0 40px 40px;
  }

  .partial .header-image img{
    height: 100px;
  }

  .partial .header-image{
    right: 10vw;
    top: 5vh;
  }

  /** Header with none height */

  .none {
    height: 5vh;
    border-radius: 0 0 20px 20px;
  }

  .none .header-image{
    display: none;
  }

  .none .header-text{
    display: none;
  }

  /** Header text */

  .header-text{
    position: absolute;
    bottom: 5%;
    width: 100%;
    padding: 0 10%;
    font-family: 'Work sans', sans-serif;
  }

  .header .greeting{
    font-size: 1rem;
    line-height: 2rem;
    font-weight: 100;
    text-transform: uppercase;
  }

  .header .name{
    font-size: 2rem;
    text-transform: capitalize;
  }

  .morning .header-text{
    animation: right_to_left 2s ease;
  }

  .afternoon .full .header-text{
    text-align: center;
    animation: left_to_right 2s ease;
  }

  .evening .full .header-text, .night .full .header-text{
    text-align: right;
    animation: left_to_right 2s ease;
  }

  /**Header text with partial height */

  .partial .header-text{
    text-align: left;
  }

  /** Body */

  .body{
    margin-top: 55vh;
  }

  @-webkit-keyframes mover {
    0% { -webkit-transform: translateY(0); }
    100% { -webkit-transform: translateY(-20px); }
  }

  @keyframes mover {
      0% { transform: translateY(0); }
      100% { transform: translateY(-20px); }
  }

  @keyframes right_to_left {
    from {
      opacity: 0;
      margin-left: 60%;
    }
    to {
      opacity: 1;
      margin-left: 0;
    }
  }

  @keyframes left_to_right {
    from {
      opacity: 0;
      margin-left: -60%;
    }
    to {
      opacity: 1;
      margin-left: 0;
    }
  }

  @-webkit-keyframes right_to_left {
    from {
      opacity: 0;
      margin-left: 60%;
    }
    to {
      opacity: 1;
      margin-left: 0;
    }
  }

  @-webkit-keyframes left_to_right {
    from {
      opacity: 0;
      margin-left: -60%;
    }
    to {
      opacity: 1;
      margin-left: 0;
    }
  }

</style>
