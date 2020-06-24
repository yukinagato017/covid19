<template>
  <div :style="bannerStyle" class="home">
    <div v-if="errored">
      <h1>Sorry unable to load resources. Please Try Again</h1>
    </div>
    <div class="loading" v-else><h1 v-if="loading">Loading...</h1></div>
    <div class="content" v-if="typeof summary.data != 'undefined'">
      <h3>Covid 19 Summary Update</h3>
      <h1>{{ summary.data.total_cases }}</h1>
      <h6 class="cases">Cases</h6>
      <div class="content-text">
        <h4>Recovered: {{ summary.data.recovery_cases }}</h4>
        <h4>Deaths: {{ summary.data.death_cases }}</h4>
      </div>
    </div>
    <HelloWorld />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";

export default {
  data() {
    return {
      summary: "",
      bannerStyle: {
        backgroundImage: `url(${require("@/assets/brian-mcgowan-7OabDHeImsA-unsplash.jpg")})`,
        backgroundSize: "cover",
        backgroundPosition: "center center"
      },
      loading: true,
      errored: false
    };
  },
  mounted() {
    axios
      .get(
        "https://corona-virus-stats.herokuapp.com/api/v1/cases/general-stats"
      )
      .then(response => {
        this.summary = response.data;
      })
      .catch(error => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
  components: {
    HelloWorld
  }
};
</script>
<style lang="scss" scoped>
$mobile: 700px;
.home {
  background-color: #34495e;
  position: absolute;
  width: 100%;
  text-align: center;
}
h3 {
  color: #fff;
  text-align: center;
}
.content {
  color: #fff;
  text-align: center;
  font-size: 30px;
}
.cases {
  top: -50px;
  position: relative;
}
.content-text {
  position: relative;
  display: inline-flex;
  margin: 0px 25px;
  padding: 0px 13px;
  text-indent: 3vw;
  text-align: center;
  top: -29px;
}
.loading {
  position: relative;
  h1 {
    color: #fff;
  }
}
@media screen and (max-width: $mobile) {
  .content-text {
    display: block;
  }
}</style
>>
