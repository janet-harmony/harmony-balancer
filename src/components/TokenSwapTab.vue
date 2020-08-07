<template>
    <v-container fluid>
        <v-container align="center" justify="center">
        <v-card width="500">
            <v-card-title>Swap Tokens</v-card-title>
            <v-card-text>
                <v-container>
                    <v-row v-if="reverse">
                        <v-col>
                            <p>Token To Sell</p>
                            <TokenCard :tokenIcon="tokens[0].icon" :tokenName="tokens[0].name"></TokenCard>
                            <v-text-field
                                    placeholder="1"
                                    type="number"
                                    :suffix="tokens[0].name"
                                    v-model="tradeAmount">
                            </v-text-field>
                        </v-col>
                        <v-col>
                            <v-container fill-height fluid>
                                <v-container align="center" justify="center">
                                    <v-icon large>mdi-swap-horizontal</v-icon>
                                </v-container>
                            </v-container>
                        </v-col>
                        <v-col>
                            <p>Token To Buy</p>
                            <TokenCard :tokenIcon="tokens[1].icon" :tokenName="tokens[1].name"></TokenCard>
                            <p v-if="estimatedReturnTokens"> {{ estimatedReturnTokens }} {{ tokens[1].name }}</p>
                        </v-col>
                    </v-row>
                    <v-row v-else>
                        <v-col>
                            <p>Token To Sell</p>
                            <TokenCard :tokenIcon="tokens[1].icon" :tokenName="tokens[1].name"></TokenCard>
                            <v-text-field
                                    placeholder="1"
                                    type="number"
                                    :suffix="tokens[1].name"
                                    v-model="tradeAmount">
                            </v-text-field>
                        </v-col>
                        <v-col>
                            <v-container fill-height fluid>
                                <v-container align="center" justify="center">
                                    <v-icon large>
                                        mdi-swap-horizontal
                                    </v-icon>
                                </v-container>
                            </v-container>
                        </v-col>
                        <v-col>
                            <p>Token to Buy</p>
                            <TokenCard :tokenIcon="tokens[0].icon" :tokenName="tokens[0].name"></TokenCard>
                            <p v-if="estimatedReturnTokens"> {{ estimatedReturnTokens }} {{ tokens[0].name }}</p>
                        </v-col>
                    </v-row>
                </v-container>
            </v-card-text>
            <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn class="ma-2" tile @click="estimateReturn">Estimate</v-btn>
                <v-btn class="ma-2" tile @click="reverseTrade">Reverse</v-btn>
                <v-btn class="ma-2" tile @click="swapTokens">Swap</v-btn>
            </v-card-actions>
        </v-card>
        </v-container>
    </v-container>
</template>

<script>
    import TokenCard from "./TokenCard";
    export default {
        name: 'TokenSwapTab',
        components: {TokenCard},

        props: {
            tokens: Array,
        },

        data() {
            return {
                reverse: true,
                tradeAmount: 0,

                estimatedReturnTokens: 0,
            }
        },

        methods: {
            reverseTrade() {
                this.reverse = !this.reverse
            },
            swapTokens() {
                console.log('Swap ' + this.tradeAmount + ' tokens' )
            },
            estimateReturn() {
                console.log('Estimate return value')
            }
        }
    };
</script>