<template>
    <v-container fluid>
        <v-container align="center" justify="center">
            <v-card width="1000" v-if="displayPool">
                <v-card-title>Liquidity Pool</v-card-title>
                <v-card-text>
                    <v-container>
                        <v-row>
                            <v-col>
                                <p>50%</p>
                            </v-col>
                            <v-col>
                                <TokenCard :tokenIcon="tokens[0].icon" :tokenName="tokens[0].name"></TokenCard>
                            </v-col>
                            <v-col>
                                <p>50%</p>
                            </v-col>
                            <v-col>
                                <TokenCard :tokenIcon="tokens[1].icon" :tokenName="tokens[1].name"></TokenCard>
                            </v-col>
                            <v-col>
                                <v-row>
                                    <p>Pool Address</p>
                                </v-row>
                                <v-row>
                                    <p>{{ poolAddress }}</p>
                                </v-row>
                            </v-col>
                            <v-col>
                                <v-row>
                                    <p>Swap Fee</p>
                                </v-row>
                                <v-row>
                                    <p>{{ swapFee }}%</p>
                                </v-row>
                            </v-col>
                        </v-row>
                    </v-container>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn class="ma-2" tile @click="displayJoinCard">Join Pool</v-btn>
                    <v-btn class="ma-2" tile @click="displayExitCard">Exit Pool</v-btn>
                </v-card-actions>
            </v-card>
            <v-card max-width="500" v-if="displayJoin">
                <v-card-title>Join Liquidity Pool</v-card-title>
                <v-card-text>
                    <v-row>
                        <v-col>
                            <TokenCard :tokenIcon="tokens[0].icon" :tokenName="tokens[0].name"></TokenCard>
                            <v-text-field
                                    placeholder="1"
                                    type="number"
                                    :suffix="tokens[0].name"
                                    v-model="joinAmount">
                            </v-text-field>
                        </v-col>
                        <v-col>
                            <TokenCard :tokenIcon="tokens[1].icon" :tokenName="tokens[1].name"></TokenCard>
                            <p>{{ joinAmount }} {{ tokens[1].name}}</p>
                        </v-col>
                    </v-row>
                </v-card-text>
                <v-card-actions>
                    <v-btn class="ma-2" tile @click="displayOnlyPool">Cancel</v-btn>
                    <v-spacer></v-spacer>
                    <v-btn class="ma-2" tile @click="joinPool">Join Pool</v-btn>
                </v-card-actions>
            </v-card>
            <v-card max-width="500" v-if="displayExit">
                <v-card-title>Join Liquidity Pool</v-card-title>
                <v-card-text>
                    <v-text-field
                            placeholder="1"
                            type="number"
                            :suffix="tokens[0].name"
                            v-model="exitAmount">
                    </v-text-field>
                    <v-row>
                        <v-col>
                            <TokenCard :tokenIcon="tokens[0].icon" :tokenName="tokens[0].name"></TokenCard>
                        </v-col>
                        <v-col>
                            <TokenCard :tokenIcon="tokens[1].icon" :tokenName="tokens[1].name"></TokenCard>
                        </v-col>
                    </v-row>
                </v-card-text>
                <v-card-actions>
                    <v-btn class="ma-2" tile @click="displayOnlyPool">Cancel</v-btn>
                    <v-spacer></v-spacer>
                    <v-btn class="ma-2" tile @click="exitPool">Exit Pool</v-btn>
                </v-card-actions>
            </v-card>
        </v-container>
    </v-container>
</template>

<script>
    import TokenCard from "./TokenCard";
    export default {
        name: 'LiquidityPoolTab',
        components: {TokenCard},
        props: {
            tokens: Array,
        },

        data() {
            return {
                poolAddress: "0xabc",
                swapFee: 5,

                joinAmount: 0,
                exitAmount: 0,

                displayPool: true,
                displayJoin: false,
                displayExit: false,
            }
        },

        methods: {
            displayJoinCard() {
                this.displayExit = false
                this.displayPool = false
                this.displayJoin = true
            },
            displayExitCard() {
                this.displayPool = false
                this.displayJoin = false
                this.displayExit = true
            },
            displayOnlyPool() {
                this.displayExit = false
                this.displayJoin = false
                this.displayPool = true
            },
            joinPool() {
                console.log("Join pool")

                this.displayOnlyPool()
            },
            exitPool() {
                console.log("Exit pool")

                this.displayOnlyPool()
            }
        },
    };
</script>