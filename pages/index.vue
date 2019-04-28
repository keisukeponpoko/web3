<template>
  <section class="container">
    <div>
      <h1 class="title">web3</h1>
      <h2 class="subtitle">My stupendous Nuxt.js project</h2>
    </div>
  </section>
</template>

<script>
export default {
  async mounted() {
    // If the user has MetaMask:
    if (typeof web3 === 'undefined') {
      alert('metamask か、web3 ブラウザでこのページを開いてね！！');
      return;
    }

    if (typeof window.ethereum !== 'undefined') {
      alert('metamaskを多分使ってるよ');
    } else {
      alert('metamaskを多分使ってないよ');
    }

    // metamaskのログインポップアップ起動
    alert('metamask使ってる?');
    alert(ethereum.isMetaMask);
    const v = await ethereum.enable();
    console.log(v);

    web3.eth.getAccounts((error, accounts) => {
      if (error) return;
      alert(accounts);
      let user_account = accounts[0];
      if (typeof user_account !== 'undefined') {
        web3.eth.getBalance(user_account, function(err, balance) {
          const b = web3.fromWei(balance, 'ether') + ' ETH';

          alert(b);
        });
      } else {
        alert('ログインして下さい');
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
