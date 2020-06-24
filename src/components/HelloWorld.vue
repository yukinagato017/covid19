<template>
  <div class="hello">
    <h1>Today's Summary</h1>
    <span>Last Updated {{ todaySummary.data.last_update }}</span>
    <div class="summary">
      <div class="column-1">
        <h3>New Confirmed Cases</h3>
        <p>{{ todaySummary.data.rows[0].new_cases }}</p>
      </div>

      <div class="column-2">
        <h3>New Deaths</h3>
        <p>{{ todaySummary.data.rows[0].new_deaths }}</p>
      </div>

      <div class="column-3">
        <h3>Active Cases</h3>
        <p>{{ todaySummary.data.rows[0].active_cases }}</p>
      </div>
    </div>

    <div class="search-row">
      <h2>By Countries</h2>
      <input type="text" placeholder="Search Country" v-model="query" />
      <div class="table-mobile">
        <table>
          <tr>
            <td><b>Country</b></td>
            <td><b>New Confirmed</b></td>
            <td><b>Total Confirmed</b></td>
            <td><b>New Deaths</b></td>
            <td><b>Total Deaths</b></td>
            <td><b>New Recovered</b></td>
            <td><b>Total Recovered</b></td>
          </tr>
          <tr v-for="row in filterSearch" :key="row.id">
            <td>{{ row.Country | to-lowercase }}</td>
            <td>{{ row.NewConfirmed }}</td>
            <td>{{ row.TotalConfirmed }}</td>
            <td>{{ row.NewDeaths }}</td>
            <td>{{ row.TotalDeaths }}</td>
            <td>{{ row.NewRecovered }}</td>
            <td>{{ row.TotalRecovered }}</td>
          </tr>
        </table>
      </div>
    </div>

    <div class="news-row">
      <h2>Covid19 News around the World</h2>
      <div class="news-column-wrapped" v-for="news in articles" :key="news.id">
        <div class="news-img">
          <img class="img" v-if="news.urlToImage" :src="news.urlToImage" />
        </div>
        <div class="news-details">
          <a v-if="news.url" :href="news.url">
            <strong>{{ news.title }}</strong></a
          >
          <p>{{ news.description }}</p>
          <p>{{ news.source.name }}</p>
        </div>
      </div>
    </div>

    <div class="image-div" :style="banner">
      <h2>Let's Help each other to STOP Covid-19</h2>
    </div>
    <Footer />
  </div>
</template>

<script>
import axios from "axios";
import Footer from "@/components/Footer.vue";

export default {
  name: "HelloWorld",
  components: {
    Footer
  },
  data() {
    return {
      todaySummary: "",
      api_key: "85cfd54a7ea44031abc024a0f87c029f",
      Countries: [],
      articles: [],
      banner: {
        backgroundImage: `url(${require("@/assets/3688262.jpg")})`,
        backgroundPosition: "center",
        backgroundRepeat: "no-repeat",
        backgroundSize: "cover"
      },
      query:""
    };
  },

  mounted() {
    var self = this;
    axios
      .get(
        "https://corona-virus-stats.herokuapp.com/api/v1/cases/countries-search"
      )
      .then(response => {
        this.todaySummary = response.data;
      });
    axios.get("https://api.covid19api.com/summary").then(response => {
      this.todaySummary = response.data;
      self.Countries = response.data.Countries;
    });
    axios
      .get(
        "https://newsapi.org/v2/everything?q=COVID&sortBy=publishedAt&apiKey=" +
          this.api_key +
          "&pageSize=3&page=2"
      )
      .then(response => {
        self.articles = response.data.articles;
      });
  },
  computed: {
    filterSearch() {
      return this.Countries.filter((row) => {
        return row.Country.match(this.query)
      })
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$mobile: 700px;
.hello {
  background-color: #fff;
  width: 100%;
  margin: 14px 0px;
  position: absolute;
  text-align: center;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.summary {
  text-align: center;
  width: 100%;
  display: flex;
  overflow: hidden;

  .column-1 {
    width: 33%;
  }
  .column-2 {
    width: 33%;
  }
  .column-3 {
    width: 33%;
  }
}
.search-row {
  width: 100%;
  margin: 70px 0px;
}
input[type="text"] {
  width: 65%;
  padding: 8px 5px;
  outline: none;
  outline-style: none;
  border-radius: 5px;
  border: 1px solid;
  text-transform:capitalize;
}
.table-mobile {
  overflow: auto;
}
table {
  width: 90%;
  margin: 52px;
  height: 1;
  border-collapse: collapse;

  td,
  tr {
    border: 1px solid #cacfd2;
    color: black;
    padding: 10px;
  }
  tr:nth-child(even) {
    background-color: #dddddd;
  }
}
.news-column-wrapped {
  background-color: #d7dbdd;
  position: relative;
  width: 90%;
  display: inline-flex;
  height: auto;
  margin: 5px;
  border-radius: 6px;

  .news-img {
    background-color: #99a3a4;
    width: 26%;
  }
  .news-details {
    width: 100%;
    text-align: left;
    padding: 3px 11px;
    margin: 6px 0px -8px 0px;

    a {
      color: #000;
      text-decoration: none;
    }
  }
  .img {
    width: 100%;
    height: 100%;
  }
}
.image-div {
  width: 100%;
  height: 30vw;
  margin: 4vw 0px 0px 0px;

  h2 {
    padding: 20px 0px 0px 0px;
    color: #f5b041;
  }
}
@media screen and (max-width: $mobile) {
  .summary {
    display: inline-block;

    .column-1 {
      width: 100%;
    }
    .column-2 {
      width: 100%;
    }
    .column-3 {
      width: 100%;
    }
  }
  table {
    overflow-x: hidden;
  }
  .news-column-wrapped {
    display: block;
    margin: 30px 0px 0px 26px;

    .news-img {
      width: 100%;
    }
    .news-details {
      width: 90%;
      text-align: left;
      padding: 7px 23px;
    }
  }
}
.table-mobile {
  overflow: auto;
}
</style>
