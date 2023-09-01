<template>
  <ClientOnly>
    <div>
      <WalletMultiButton />
      <p>{{ publicKey ? publicKey.toBase58() : "Not connected" }}</p>
      <p>{{ balance }}</p>
    </div>
  </ClientOnly>
</template>

<script setup>
import { ref } from 'vue';
import { WalletMultiButton,useWallet } from 'solana-wallets-vue';
import { Connection, clusterApiUrl } from '@solana/web3.js';
const { publicKey, connected } = useWallet();
const balance = ref(0);
const fetchBalance = async () => {
  const connection = new Connection(clusterApiUrl('devnet'));
  balance.value = connected.value ? await connection.getBalance(publicKey.value) : 0;
};
watch(connected,fetchBalance);
</script>
