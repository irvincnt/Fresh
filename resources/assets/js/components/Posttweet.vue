<template>
    <form action="#" v-on:submit.prevent="post" >
        <div class="form-group">
            <textarea name="" id="" cols="30" rows="2" class="form-control" v-model="body"></textarea>
            <br>                   
            <button class="btn btn-default" type="submit">Post</button>
        </div>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                body: null
            }
        },
        props: [
            'tweets'
        ],
        methods: {
            post: function () {
                this.$http.post('/tweets', {body: this.body,
                headers: {
                        'Content-Type': 'application/json',
                        'Accept': 'application/json'
                }
                }).then((response) => {
                    this.tweets.unshift(response.body);
                    this.body = null
                });
            }
        }
    }
</script>