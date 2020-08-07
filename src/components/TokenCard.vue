<template>
    <v-card>
        <v-card-text>
            <v-img v-bind:src="tokenIcon" height="50" width="50"></v-img>
            <p>{{ tokenName }}</p>
        </v-card-text>
    </v-card>
</template>

<script>
    export default {
        name: 'TokenCard',

        props: {
            tokenIcon: String,
            tokenName: String,
        },
    };
</script>