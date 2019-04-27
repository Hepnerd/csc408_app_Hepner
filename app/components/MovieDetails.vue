<template>


    <FlexboxLayout flexDirection="row" class="list-group-item">
        <GridLayout @onTap="onTap" columns="3*, 7*" rows="*,*" width="100%" >
            <Image @onTap="onTap" :src="imageUrl" row="0" col="0" rowSpan="4"  class="thumbnail"/>

            <Label @onTap="onTap" :text="movie.length + ' minutes long'" row="1" col="2" class="label-text" style="padding-left: 10%" />


            <Label @onTap="onTap" :text="movie.title" row="0" col="4" class="label-text" style="padding-left: 10%" />
        </GridLayout>
    </FlexboxLayout>
</template>

<script>
    import MovieRentals from '@/components/MovieRentals';

    export default {
        data() {
            return {}
        },
        methods: {
            onTap: function () {
                this.$navigateTo(MovieRentals, {
                    props: {
                        id: this.movie.id
                    }
                });

            }
        },
        computed: {
        imageUrl: function(){
          return "https://codeflare.tech/images/movie_" + this.movie.id + ".jpg";
        }
        },
        props: ['movie'],
        components: {
            MovieRentals
        },
        mounted() {
        }
    }
</script>

<style scoped>
    .label-text {
        font-size: 14;
        color: #444444;
    }
</style>
