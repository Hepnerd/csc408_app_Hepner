<template>
    <GridLayout columns="*, *" rows="auto" width="100%">
        <Label @onTap="onTap" :text="customer.name" row="0" col="0" class="list-group-item-heading label-text"
               style="width: 60%"/>
        <Label @onTap="onTap" :text="customer.email" row="0" col="1" class="list-group-item-heading label-text"
               style="width: 60%"/>
    </GridLayout>
</template>

<script>
    import CustomerRentals from '@/components/CustomerRentals';

    export default {
        data() {
            return {}
        },
        methods: {
            onTap: function () {
                // console.log("Item with name: " + this.customer.name + " tapped");
                this.$navigateTo(CustomerRentals, {
                    props: {
                        id: this.customer.id
                    }
                });

            }
        },
        props: ['customer'],
        components: {
            CustomerRentals
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
