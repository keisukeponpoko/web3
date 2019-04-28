<template>
  <section class="container">
    <div>
      <h1 class="title">web3</h1>
      <h2 class="subtitle">My stupendous Nuxt.js project</h2>
    </div>
  </section>
</template>

<script>
import web3 from 'web3';

export default {
  async mounted() {
    // If the user has MetaMask:
    if (typeof window.web3 === 'undefined') {
      console.error('You need to install MetaMask for this app to work!');
      return;
    }

    window.ethereum.enable();
    console.log(window.web3);
    const net = new Web3(window.web3.currentProvider);
    console.log(net);

    net.eth.getAccounts((error, accounts) => {
      if (error) return;
      console.log(accounts);
      let user_account = accounts[0];
      if (typeof user_account !== 'undefined') {
        console.log(user_account);
        net.eth.getBalance(user_account, function(err, balance) {
          const b = net.fromWei(balance, 'ether') + ' ETH';

          console.log(b);
        });
      } else {
        console.log('ログインして下さい');
      }
    });
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
