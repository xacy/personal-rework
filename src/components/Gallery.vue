<template>
    <div class="gallery">
        <app-work v-for="work in works" :work="work"></app-work>
    </div>
</template>

<script>
    import Work from './Work.vue';

    export default {
        components: {
          'app-work':Work
        },
        data: function () {
            return {
                works: [
                    {
                        title: "Flat Pentaho B.I. redesign",
                        techs: ['html5','css3','B.I.','jsp','Pentaho'],
                        description: "Complete dashboard redesign for an internal Pentaho B.I. solution for my current employee",
                        img: '',
                        github:''
                    },
                    {
                        title: "Minimalist blog redesign",
                        techs: ['html5','css3','wordpress'],
                        description: "Custom wordpress css3 theme for a minimal experience (Early work)",
                        img: '',
                        github:''
                    },
                    {
                        title: "BBT1 shot generator",
                        techs: ['android'],
                        description: "Android app that started as an experiment and ended used in a local bar to boost the sales.",
                        img: '',
                        github:''
                    }
                    ]
            }
        }
    }
</script>

<style>
    .column .gallery{
        width:100% !important;
    }
    #section3 .fp-tableCell {
        vertical-align: middle !important;
    }
    .gallery{
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: left;
        align-items: center;
    }

</style>