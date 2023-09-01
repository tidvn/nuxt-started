<script lang="ts" setup>
import { WalletMultiButton } from "solana-wallets-vue";
</script>

<template>
  <ClientOnly>
    <WalletMultiButton />
  </ClientOnly>
</template>