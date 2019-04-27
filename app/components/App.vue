<template>
    <Page>
        <ActionBar title="Welcome to Nathanael's Yellow Bucket!" android:flat="true" style="background-color:#272324;color:#E4D8B4"/>
        <TabView tabBackgroundColor="#E2CD6D"
                 androidSelectedTabHighlightColor="#ffffff"
                 tabTextColor="#83B799"
                 selectedTabTextColor="#E86F68">
            <TabViewItem title="Movies">
            <movie-component :movies="movies"></movie-component>
            </TabViewItem>
            <TabViewItem title="Customers">
                <customer-component :customers="customers"></customer-component>
            </TabViewItem>
            <TabViewItem title="About">
                <GridLayout columns="*" rows="*">
                    <Label class="message" text="Building an app isn't as easy as it looks" col="0" row="0"/>
                </GridLayout>
            </TabViewItem>
        </TabView>
    </Page>
</template>

<script>
    import axios from "axios";
    import MovieComponent from '@/components/MovieComponent.vue';
    import CustomerComponent from '@/components/CustomerComponent.vue';

    function Movie({id, title, length, description})
    {
    this.id = parseInt(id);
    this.title = title;
    this.length = length;
    this.description = description;
    }

    function Customer({id, name, email, isAdmin}) {
        this.id = parseInt(id);
        this.name = name;
        this.email = email;
        this.isAdmin = isAdmin
    }

    export default {
        data() {
            return {
                msg: 'This is where you put you Movie code!  Good luck!',
                customers: [],
                movies: []
            }
        },
        methods: {
            onItemTap: function (args) {
                console.log("Item with index: " + args.index + " tapped");
            }
        },
        mounted() {
            axios.get("https://codeflare.tech/api/customers").then(result => {
                result.data.forEach(customer => {
                    this.customers.push(new Customer(customer));
                })
            }, error => {
                console.error(error);
            }),
            axios.get("https://codeflare.tech/api/movies").then(result => {
                result.data.forEach(movie => {
                    this.movies.push(new Movie(movie));
                })
            }, error => {
                console.error(error);
            })

        },
        components: {
            CustomerComponent,
            MovieComponent
        }
    }
</script>

<style scoped>
    ActionBar {
        background-color: #666666;
        color: #fafafa;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #666666;
    }

    .label-text {
        color: #444444;
    }
</style>
