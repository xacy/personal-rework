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
    }
</style>