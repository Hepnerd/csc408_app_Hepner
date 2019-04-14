<template>
    <FlexboxLayout flexDirection="row" class="list-group-item">
        <GridLayout columns="3*,7*" rows="*,*,*,*" width="100%" >
            <Image :src="imageUrl" row="0" col="0" rowSpan="4"  class="thumbnail"/>

            <Label :text="this.rental.title" row="0" col="1" class="label-text" />
            <Label :text="this.rental.rating" row="1" col="1" class="label-text" />
            <Label :text="'Rented: ' + rented" row="2" col="1" class="label-text" />
            <Label :text="'Returned: ' + returned" row="3" col="1" class="label-text" />
        </GridLayout>
    </FlexboxLayout>
</template>

<script>
export default {
    data () {
      return {}
    },
    methods: {

    },
    computed: {
        /* Build URL for image */
        imageUrl: function(){
          return "https://codeflare.tech/images/movie_" + this.rental.transaction.movie_id + ".jpg";
        },
        /* Make a pretty date for showing last_update */
        rented: function(){
            var options = { year: 'numeric', month: 'numeric', day: 'numeric'};
            var day  = new Date(this.rental.transaction.rent_date);
            return (day.getMonth() + 1) + '/' + day.getDate() + '/' +  day.getFullYear();
        },
        /* Make a pretty date for showing last_update */
        returned: function(){
            if (this.rental.transaction.return_date == null) return '';
            var options = {year: 'numeric', month: 'numeric', day: 'numeric'};
            var day  = new Date(this.rental.transaction.return_date);
            return (day.getMonth() + 1) + '/' + day.getDate() + '/' +  day.getFullYear();
        }
    },
    props: ['rental']
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    .thumbnail { width: 50; }

    td { text-align: left; }

    .label-text { color: #000;
    }
</style>
