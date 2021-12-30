<template>
  <div>
    <div class="form-inline my-2 my-lg-0">
      <input class="form-control mr-sm-2" type="number" placeholder="Type Block number" v-model="search_address" aria-label="Search" />
      <button class="btn btn-outline-success my-2 my-sm-0" v-on:click.prevent="getTransactions()">
        Search
      </button>
    </div>
    <div id="serchResukt" v-test="serchResult">

    </div>
  </div>
</template>


<script>
export default {
  name: 'ViewTxs',
  data(){
    return {
      search_address: "",
      serchResult:""
    }
  },
  methods: {
    getTransactions: function() {
      if(this.search_address !== "") {
        GetBlockinfo(this.search_address);
      }
    }
  }
}


var Web3 = require("web3")
const web3 = new Web3("https://cloudflare-eth.com")

//ブロックの最新トランザクションを表示する関数
async function GetBlockinfo(blockNumber){
  var blockInfo = await web3.eth.getBlock(blockNumber);
  var txCountByBlockNum = await web3.eth.getBlockTransactionCount(blockNumber);
  if(txCountByBlockNum != 0){
    var txInfo =web3.eth.getTransaction(blockInfo.transactions[txCountByBlockNum-1]);
    console.log(txInfo);
  }else{
    console.log('このブロックにトランザクションはありません。');
  }
  
  //web3.eth.getTransaction(blockInfo.transactions[0]).then(console.log);
}
/*
0xb18b0ab693ac3942c70d5d6d8f0ed85649eb5ce23f66138e7df32b601857d01f
0xb18b0ab693ac3942c70d5d6d8f0ed85649eb5ce23f66138e7df32b601857d01f

0x0b660cfa8d754cb9180a7a27d72b22f2d48a85fecd1e142efb6c676b3ce49c8f
0x0b660cfa8d754cb9180a7a27d72b22f2d48a85fecd1e142efb6c676b3ce49c8f
async function GetTransactionsByAccount(address){
    var myAddr = address;
    let latestBlock = await web3.eth.getBlock('latest');
    console.log(latestBlock);
    var currentBlock = latestBlock.number;
    console.log(currentBlock);
    var n = await web3.eth.getTransactionCount(myAddr, currentBlock);
    console.log(n);
    //var bal = await web3.eth.getBalance(myAddr, currentBlock);

    /*
    for (var i=currentBlock; i >= 0 && (n > 0 || bal > 0); --i) {
        try {
            var block = web3.eth.getBlock(i, true);
            if (block && block.transactions) {
                block.transactions.forEach(function(e) {
                    if (myAddr == e.from) {
                        if (e.from != e.to)
                            bal = bal.plus(e.value);
                        console.log(i, e.from, e.to, e.value.toString(10));
                        --n;
                    }
                    if (myAddr == e.to) {
                        if (e.from != e.to)
                            bal = bal.minus(e.value);
                        console.log(i, e.from, e.to, e.value.toString(10));
                    }
                });
            }
        } catch (e) { console.error("Error in block " + i, e); }
    }
    */

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
