<template>
    <div class="hello">
        <h1>Welcome to Your Vue.js Dapp</h1>
        <div v-if="state.status">
            <button @click="connectUserWallet" class="button">Connected</button>
            <h3>Address: {{stete.address}}</h3>
            <h3>ChainId: {{state.chainId}}</h3>
            <button class="disconnect__button">Disconnect</button>

        </div>
        <button v-else @click="connectUserWallet" class="button">Connect Wallet</button>

    </div>
</template>

<script>
import connect from '../composables/connect/index';
export default {
  name: 'StatusContainer',
  setup: () => {
    const { connectWalletConnect, disconnectWallet, state } = connect();
    const connectUserWallet = async () => {
      await connectWalletConnect();
    };

    const disconnectUser = async() => {
      await disconnectWallet()
    }
    return {
      connectUserWallet,
      disconnectUser,
      state
    }
  }
}
</script>