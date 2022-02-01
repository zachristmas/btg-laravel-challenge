<template>
    <div class="container">
    <br>
    <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">BTG Laravel Challenge</div>

                    <div class="card-body">
                        <h4>Challenge is broken up into 3 parts:</h4>
                        <ol>
                            <li>Get connected to the development server.</li>
                            <li>Create API Controller to GET items from <strong>articles</strong> table in the <strong>laravel</strong> mysql database.</li>
                            <li>Call API controller from this component and render it below.</li>
                        </ol>
                        <p>
                            Feel free to ask questions or google as you would doing this on your own.
                        </p>
                    </div>
                </div>
            </div>
        </div>
        <br>
        <hr>
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div class="card-header">Articles Should Render Below</div>

                    <div class="card-body">
                        <ul id="example-1">
                            <li v-for="article in articles" :key="article.id">
                                {{ article.title }}
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
        data: function () {
            return {
                articles: []
            }
        },
        mounted() {
            console.log('Welcome to the BTG Challenge!.');
            axios.get('/api/articles')
            .then((response) => {
                // handle success
                this.articles = response.data;
            })
            .catch((error) => {
                // handle error
                console.log(error);
            })
            .then(() => {
                // always executed
            });
        }
    }
</script>
