<template>
  <div>
    <div class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="text" placeholder="Type Block number" v-model="search_address" aria-label="Search" />
      <button class="btn btn-outline-success my-2 my-sm-0" v-on:click.prevent="getTransactions()">
        Search
      </button>
    </div>
  </div>
</template>


<script>
export default {
  name: 'ViewTxs',
  data(){
    return {
      search_address: ""
    }
  },
  methods: {
    getTransactions: function() {
      if(this.search_address !== "") {
        web3.eth.getTransaction(this.search_address)
        .then(console.log);
      }
    }
  }
}


var Web3 = require("web3")
const web3 = new Web3("https://cloudflare-eth.com")
/*
web3.eth.getBlockNumber(function (error, result) {
  console.log(result)
})

 web3.eth.getBlock(13867957)
 .then(console.log);

web3.eth.getBlockTransactionCount(13867957)
.then(console.log);

web3.eth.getTransaction('0x4ec5a35de5a55dcfedba544bdf1d60576a57611744afa6ab9b9000cc8649c0a9')
.then(console.log);

for (var i=13867950; i<13867957; i++) {

  const txData = web3.eth.getBlock(i);
  console.log(txData);

}
*/
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
