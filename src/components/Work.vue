<template>
    <div class="work" @click="clickEvent">
        <p class="title">
            {{ work.title }}
        </p>
        <div class="techs">
            {{ work.techs}}
        </div>
    </div>
</template>

<script>
    export default {
        props: {
            work: {}
        },
        methods: {
            clickEvent(){
                alert(this.work);
            }
        }
    }
</script>

<style scoped>
    .work{
        cursor: pointer;
        margin: 0.7em;
        flex-direction: row;
        box-shadow: 0 4px 4px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        padding: 1em 2em;
        flex-basis: 25em;
    }

    /* On mouse-over, add a deeper shadow */
    .work:hover {
        box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
    }
    .techs{
        margin-top:1em;
    }
</style>