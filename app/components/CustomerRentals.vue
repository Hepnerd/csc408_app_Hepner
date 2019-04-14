<template>
    <Page>
        <ActionBar :title="'Rentals for ' + customer_name" android:flat="true"/>
        <ListView for="rental in rentals" class="list-group" style="height:100%">
            <v-template>
                <customer-rental-history :rental="rental"></customer-rental-history>
            </v-template>
        </ListView>
    </Page>
</template>
<script>

    function Rental({id, title, rating, length, pivot}) {
        this.id = parseInt(pivot.id)
        this.title = title
        this.rating = rating
        this.length = length
        this.transaction = pivot
    }

    import axios from "axios";
    import CustomerRentalHistory from '@/components/CustomerRentalHistoryComponent.vue'

    export default {
        data() {
            return {
                customer_name: '',
                rentals: []
            }
        },
        methods: {
            read() {
                let url = 'https://codeflare.tech/api/customers/' + this.id + '/rentals'
                axios.get(url).then(({data}) => {
                    this.customer_name = data[0].name;

                    console.log('Name is: ' + this.customer_name + '-------');
                    // console.log(data[0]);
                    data[0].rentals.forEach(rental => {
                        this.rentals.push(new Rental(rental))
                    });

                }, error => {
                    console.error(error);
                })
            }
        },
        components: {
            CustomerRentalHistory
        },
        props: ['id'],
        created() {
            this.read()
        }
    }
</script>

<style scoped lang="scss">

</style>
