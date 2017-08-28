<template>
    <div class="container">
        <div class="row">
            <div class="col-md-8 col-md-offset-2">
                <div class="panel panel-default">
                    <div class="panel-heading">TimeLine</div>
                    <div class="panel-body">
                    <posttweet :tweets="tweets"></posttweet> 
                    <hr class="my-4">
                        <div class="media" v-for="tweet in tweets">
                            <div class="media-left">
                                <a href="">
                                    <img src="https://pbs.twimg.com/profile_images/827790443152805888/hy08L7YR_bigger.jpg" alt="">
                                </a>
                            </div>
                            <div class="media-body">
                                <strong>{{tweet.user.name}}</strong>
                                <p>{{tweet.body}}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Posttweet from './Posttweet.vue'

    export default {
        data () {
            return {
                tweets: []
            }
        },
        components: [
            Posttweet
        ],
        mounted() {
            this.$http.get('/tweets').then((response) => {
                this.tweets = response.body
            })
        }
    }
</script>
