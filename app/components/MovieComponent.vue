<template>
    <ListView for="movie in movies" class="list-group" style="height:1250px">
        <v-template>
            <FlexboxLayout flexDirection="row" class="list-group-item">
                <movie-details :movie="movie"></movie-details>
            </FlexboxLayout>
        </v-template>
    </ListView>
</template>

<script>
    import MovieDetails from '@/components/MovieDetails.vue';
    export default {
        data() {
            return {}
        },
        methods: {
            onNameTap: function (args) {
                console.log("Item with id: " + args.item.id + " tapped");
                // console.log(args);
            }
        },
        props: ['movies'],
        components: {
            MovieDetails
        },
        mounted() {
        }
    }
</script>

<style scoped>
    .label-text {
        color: #444444;
    }
    list-group {
          content: "";
          position: fixed;
          top: -10px;
          left: 0;
          width: 100%;
          height: 10px;

          -webkit-box-shadow: 0px 0px 20px rgba(0,0,0,.8);
              -moz-box-shadow: 0px 0px 20px rgba(0,0,0,.8);
                         box-shadow: 0px 0px 20px rgba(0,0,0,.8);

          z-index: 100;
}
</style>
