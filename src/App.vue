<template>
    <div id="app">
        <div class="container">
            <account-exec
                :profile="execs[0]"
            />
            <account-exec
                :profile="execs[1]"
            />
            <img
                class="needle"
                :class="nextUp.name"
                src="./assets/gauge-needle.png">
        </div>

        <button
            type="button"
            name="switch ae"
            @click="switchAe()">
            Give next opp to {{nextUp.name}}
        </button>
    </div>
</template>

<script>
import AccountExec from './components/account-exec.vue';

export default {
    name: 'app',
    components: {
        AccountExec
    },
    data () {
        return {
            execs: [
                {
                    name: 'sandy',
                    next: false,
                    lastOpp: new Date()
                },
                {
                    name: 'wilson',
                    next: true,
                    lastOpp: new Date()
                },
            ]
        };
    },
    computed: {
        nextUp () {
            if (this.execs) {
                let next = this.execs.filter((exec) => {
                    return exec.next;
                });

                return next[0];
            }
        }
    },
    methods: {
        switchAe () {
            if (this.execs[0].next) {
                this.execs[0].next = false;
                this.execs[1].next = true;
            } else {
                this.execs[1].next = false;
                this.execs[0].next = true;
            }
        }
    }
}
</script>

<style lang="scss">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;

    .container {
        position: relative;
        display: flex;
        justify-content: center;
        padding-bottom: 100px;
    }

    .needle {
        position: absolute;
        width: 30px;
        bottom: 0;

        &.sandy {
            transform: rotate(-30deg);
        }

        &.wilson {
            transform: rotate(30deg);
        }
    }
}
</style>
