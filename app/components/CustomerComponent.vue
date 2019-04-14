<template>
    <ListView for="customer in customers" class="list-group" style="height:1250px">
        <v-template>
            <FlexboxLayout flexDirection="row" class="list-group-item">
                <customer-details :customer="customer"></customer-details>
            </FlexboxLayout>
        </v-template>
    </ListView>
</template>

<script>
    import CustomerDetails from '@/components/CustomerDetails.vue';
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
        props: ['customers'],
        components: {
            CustomerDetails
        },
        mounted() {
        }
    }
</script>

<style scoped>
    .label-text {
        color: #444444;
    }
</style>
