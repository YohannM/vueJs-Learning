<template>
    <div class="main">
        <div class="hello">
            <div class="header">Here is a nice toggle to switch between views</div>
            <div class="toggler">
                <toggler :tabs="tabs" 
                        :selected="selected"
                        @select="toggleView">
                </toggler>
            </div>
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
    import Toggler from "./Toggler.vue";

    export default {
        data() {
            return {
                tabs: [
                    {
                        tab: "",
                        label: "Default"
                    },
                    {
                        tab: "goodbye",
                        label: "GoodBye"
                    },
                    {
                        tab: "hello/Yohann",
                        label: "Hello"
                    }
                ],
                selected: ""
            };
        },
        components: {
            Toggler,
        },
        methods: {
            toggleView(tab) {
                this.selected = tab;
                this.$router.push({ path: `/${tab}`, replace: tab === '' });
            }
        }
    };
</script>

<style>
    .main {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-family: system-ui;
    }

    .hello {
        display: flex;
        justify-content: left;
        flex-direction: column;
    }

    .header,
    .toggler {
        margin-bottom: 30px;
    }
</style>
