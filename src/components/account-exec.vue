<template>
    <div class="ae-profile">
        <img class="ae-pic" :src="getSrc()">
        <span v-if="!profile.next">{{oppDisplay}}</span>
    </div>
</template>

<script>
export default {
    name: 'AccountExec',
    props: {
        profile: Object
    },
    data () {
        return {
            oppDisplay: `${this.profile.lastOpp.toDateString()} at ${this.profile.lastOpp.toLocaleTimeString()}`
        };
    },
    methods: {
        getSrc () {
            return require(`../assets/${this.profile.name}.png`);
        }
    }
}
</script>

<style scoped lang="scss">
    .ae-profile {
        display: flex;
        flex-direction: column;

        .ae-pic {
            width: 100px;
            margin: 0 30px
        }
    }
</style>
