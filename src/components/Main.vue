<template>
  <main>
    <h3 class="exchange-text">
      The current bitcoin <br />
      exchange rate: <br />
      <br />
      <span class="exchange-rate"> ${{ apiResult }} </span>
    </h3>
    <button class="refresh-button" v-on:click="refreshApiResult">
      Refresh
    </button>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",
  data() {
    return {
      apiResult: null,
    };
  },
  methods: {
    refreshApiResult() {
      axios
        .get(
          "https://min-api.cryptocompare.com/data/price?fsym=BTC&tsyms=USD&api_key=817d3ffe299d406707462fcd3ef0563a921aa0140bc4fc255dd71837384424d4"
        )
        .then((response) => {
          this.apiResult = response.data.USD;
        });
    },
  },

  mounted() {
    axios
      .get(
        "https://min-api.cryptocompare.com/data/price?fsym=BTC&tsyms=USD&api_key=817d3ffe299d406707462fcd3ef0563a921aa0140bc4fc255dd71837384424d4"
      )
      .then((response) => {
        this.apiResult = response.data.USD;
      });
  },
};
</script>

<style scoped>
.exchange-text {
  text-align: center;
  margin: 130px auto 0;
  font-size: 33px;
}
main {
  color: rgb(244, 244, 244);
  display: flex;
  flex-direction: column;
}
.exchange-rate {
  color: #129dff;
  margin-top: 15px;
  font-size: 44px;
}
.refresh-button {
  background-color: #061121;
  color: #129dff;
  border: 1px solid rgb(244, 244, 244);
  width: 130px;
  height: 50px;
  margin: 30px auto 0;
  font-size: 16px;
  cursor: pointer;
}
.refresh-button:hover {
  background-color: #061121;
  border: 1px solid #129dff;
}
</style>
