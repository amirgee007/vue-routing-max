<template>
<div>
    
    <h3>Edit the User</h3>
    <p>
        Locale: {{$route.query.locale}}
    </p>
    <p>
        Analytics: {{$route.query.q}}
    </p>
    <button class="btn btn-danger" @click="confirmed">Confirm to Ok</button>
    <p id="data"> Some Extra data</p>
</div>
    
</template>

<script>
    export default {
        data() {
            return {
                confirmed: false
            }
        },
        beforeRouteLeave(to, from, next){
            if(this.confirmed){
                next()
            } else {
                if(confirm('Are you sure to want to chinta pala?')){
                    next()
                }
                else
                {
                    next(false)
                }
            }

        },
        watch: {
            '$route'(to, from){
                this.id = to.params.id;
            }
        },
        methods: {
            navigateToHome() {
                this.$router.push({name: 'homeRoute'});
            }
            }
    }
</script>