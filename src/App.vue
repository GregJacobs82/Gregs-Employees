<template>
    <div id="app">
        <div class="small-container" id="nav">
            <router-link to="/">Home</router-link>
            |
            <router-link to="/about">About</router-link>
        </div>
        <router-view/>
        <div class="fixed-footer">
            <div class="opacity-20">
                &copy; {{ new Date().getFullYear() }} Gregory Jacobs - <a
                href="https://github.com/GregJacobs82/Filter-Map-Reduce" target="_blank"
                title="See the Github Repository">Github Repo</a>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2C3E50;
    }

    #nav {
        padding: 30px 1rem;

        a {
            font-weight: bold;
            color: #2C3E50;

            &.router-link-exact-active {
                color: #42B983;
            }
        }
    }

    .fixed-footer {
        position: fixed;
        bottom: 0;
        width: 100%;
        text-align: center;
        font-size: .85rem;
        background: rgba(250, 250, 250, 1);
        padding: 1rem;

        .opacity-20 {
            opacity: .2;
        }
    }
</style>
