<template>
  <div id="app" class="page">

    <header id="header">
      <div class="header__title">
        <h3>Simple, traffic-based pricing</h3>
      </div>
      <div class="header__content">
        <p>Sign-up for our 30-day trial.</p>
        <p>No credit card required.</p>
      </div>
    </header>
    <!-- header -->

    <main id="main">
      <Card />
    </main>
    <!-- #main -->

  </div>
  <!-- .page -->

</template>

<script lang="ts">
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    Card,
  },
};
</script>

<style lang="scss">
@import "./assets/sass/_base.scss";
@import "./assets/sass/_button.scss";

.page {
  padding: 50px 0px;
  background: url("./assets/images/bg-pattern.svg");
  background-repeat: no-repeat;
}

#header {
  height: 160px;
  background: url("./assets/images/pattern-circles.svg");
  background-repeat: no-repeat;
  background-position: center center;
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: $grayish-blue;
}

.header__title {
  h3 {
    font-size: 19px;
    color: $dark-desaturated-blue;
  }
}

.header__content {
  p {
    margin: 10px;
  }
}

#main {
  margin: 30px 20px;
}

/* Medium devices (tablets, 768px and up) */
@media (min-width: 992px) {
  .page {
    background-size: contain;
    padding: 0;
  }

  #header {
    height: 300px;
  }

  .header__title {
    h3 {
      font-size: 30px;
    }
  }

  .header__content {
    margin-top: 20px;

    p {
      font-weight: $font-bolder;
      display: inline;
      margin: 0;
    }
  }

}
</style>
