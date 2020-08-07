<template>
  <v-card class="overflow-hidden">
    <v-app-bar
            absolute
            color="#6A76AB"
            dark
            prominent
            scroll-target="#scrolling-techniques-3"
    >
      <template v-slot:img="{ props }">
        <v-img
                v-bind="props"
                gradient="to top right, rgba(0,87,116,.7), rgba(53,125,93,.7)"
        ></v-img>
      </template>

      <v-toolbar-title>Balancer Demo on Harmony</v-toolbar-title>

      <template v-slot:extension>
        <v-tabs align-with-title
                fixed-tabs>
          <v-tab href="#token-swap">Swap Tokens</v-tab>
          <v-tab href="#pool-list">Liquidity Pools</v-tab>

          <v-tab-item value="token-swap">
            <TokenSwapTab :tokens="placeholderTokens"></TokenSwapTab>
          </v-tab-item>
          <v-tab-item value="pool-list">
            <LiquidityPoolTab :tokens="placeholderTokens"></LiquidityPoolTab>
          </v-tab-item>
        </v-tabs>
      </template>
    </v-app-bar>
    <v-sheet
            id="scrolling-techniques-3"
            class="overflow-y-auto"
            max-height="600"
    >
      <v-container style="height: 1000px;"></v-container>
    </v-sheet>
  </v-card>
</template>

<script>
  import TokenSwapTab from "./components/TokenSwapTab";
  import LiquidityPoolTab from "./components/LiquidityPoolTab";

export default {
  name: 'App',

  components: {
    LiquidityPoolTab,
    TokenSwapTab
  },

  data: () => ({
    placeholderTokens: [
      {
        name: "Token A",
        icon: "https://picsum.photos/100?random"
      },
      {
        name: "Token B",
        icon: "https://picsum.photos/100?random"
      }
    ],
  }),
};
</script>