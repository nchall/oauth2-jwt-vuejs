<template>
    <div id="app">
        <nav class="navbar navbar-dark bg-dark fixed-top" v-if="user">
            <div class="container">
                <div class="navbar-header">
                    <router-link :to="{ name: 'home', params: { page: 1 } }" class="navbar-brand logo">{{title}}
                    </router-link>
                </div>

                <div class="d-flex align-items-center text-light ux-logout-block mr-1" style="display: none;">
                    <div class="small mr-3 align-self-end">
                        <div class="small">
                            <div class="small ux-use-cookie"></div>
                        </div>
                    </div>
                    <img class="mr-2 rounded-circle ux-avatar" :src="user.email | gravatar" height="30" width="30">
                    <div class="small mr-3">
                        <div class="small">WELCOME</div>
                        <h6 class="ux-username font-weight-normal m-0">{{user.username || user.name}}</h6>
                    </div>
                    <router-link :to="{ name: 'logout' }"
                                 class="d-flex align-items-center justify-content-center ux-logout"><i
                            class="fa logout-icon"></i></router-link>
                </div>
            </div>
        </nav>
        <div class="container">
            <div class="ux-content-area">
                <router-view class="view"></router-view>
            </div>
        </div>
    </div>
</template>

<script>
    module.exports = {
        data: function () {
            return {
                title: 'MovieChat'
            };
        },
        computed: {
            ...Vuex.mapState({
                user: state => state.auth.user
            })
        },
        mounted() {
        }
    }
</script>

<style>
</style>
