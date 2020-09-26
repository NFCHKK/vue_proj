<template>
    <div class="content">
        <div class="page">
            <div>
                <p>welcome entrance</p>
            </div>
            <div>
                <button @click="drawer = !drawer">点我弹框</button>
            </div>
        </div>
        <transition name="fade">
            <div class="right" v-show="drawer">
                <div class="drawer-entrance">
                    <div class="title">入口名称:</div>
                    <input v-model="dyeing.entrance" placeholder />
                </div>
                <div class="drawer-entrance">
                    <div class="title">应用:</div>
                    <input v-model="dyeing.app" placeholder />
                </div>
                <div class="drawer-entrance">
                    <div class="title">服务名称:</div>
                    <input v-model="dyeing.server" placeholder />
                </div>
            </div>
        </transition>
    </div>

</template>

<script>
    // import MainApp from '../src/App.vue'

    export default {
        name: 'search',
        components: {
           //  MainApp
        },
        data: function () {
            return {
                dyeing: {
                    entrance: "",
                    app: "",
                    server: "",
                },
                drawer: false,
            }
        }
    }
</script>
<style>
.content {
    display: flex;
    flex-direction: row;
    justify-content: left;
    overflow-x: hidden;
}
.content .page {

}
.drawer-entrance {
    display: flex;
    margin-bottom: 10px;
}

.drawer-entrance .title {
    width: 80px;
    text-align: right;
    margin-right: 10px;
}

.right {
    padding-top: 40px;
    padding-right: 40px;
    border: 1px solid #000;
    float: right;
    width: 25%;
    height: 600px;
    opacity: 1;
    position: fixed;
    right:0;
    background-color: white;
}
.fade-enter-active {
    transition: all 1s;
}

.fade-leave-active {
    transition: all 0s;
}

.fade-enter, .fade-leve-to {
    right: -25%;
}
</style>