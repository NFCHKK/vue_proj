<template>
  <div class="content">
    <div class="left">
      <anchoredhead :level="1">Hello world!</anchoredhead>
      <button v-on:click="counter += 1">Add 1</button>
      <p>The button has been clicked {{ counter }} times</p>
      <div id="example-2">
        <!-- `greet` 是在下面定义的方法名 -->
        <button v-on:click="greet">Greet</button>
      </div>
      <contact-info
        :com-email="user.DataEmail"
        :com-phone="user.DataPhone"
        :com-weibo="user.DataWeibo"
      />
      <div class="dying-table">
        <el-table :data="tableData">
          <el-table-column
            v-for="items in tableDataType"
            :key="items.nameLabel"
            :prop="items.nameProp"
            :label="items.nameLabel"
          ></el-table-column>
        </el-table>
      </div>
      <button @click="drawer = !drawer">点我打开</button>
      <button @click="drawer = !drawer">点我弹框</button>

      <!-- <div> -->
      <!-- <el-drawer :visible.sync="drawer" :direction="direction" :show-close="false">
        <div class="drawer-entrance">
          <div class="title">染色入口:</div>
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
        <div class="btn">
          <button @click="handleAdd">确定</button>
        </div>
      </el-drawer>-->
      <!-- </div> -->
    </div>
      <transition name="fade">
          <div class="right" v-show="drawer">
              <p>this is a p</p>
          </div>
      </transition>
  </div>
</template>

<script>
import anchoredhead from "../components/dyhead.vue";
import ContactInfo from "../components/contact.vue";
// import MainApp from '../src/App.vue'

export default {
  name: "dyeing-manage",
  components: {
    anchoredhead,
    ContactInfo,
    // MainApp,
  },
  data: function () {
    return {
      name: "dannykkhan",
      counter: 0,
      user: {
        DataEmail: "dannykkhan",
        DataPhone: "18320785416",
        DataWeibo: "weibo.com",
      },
      dyeing: {
        entrance: "",
        app: "",
        server: "",
      },
      drawer: false,
      direction: "rtl",
      tableDataType: [
        { nameLabel: "入口", nameProp: "entrance" },
        { nameLabel: "应用", nameProp: "app" },
        { nameLabel: "服务名称", nameProp: "server" },
        { nameLabel: "操作人", nameProp: "operator" },
      ],
      tableData: [
        {
          entrance: "第一个",
          app: "mdd",
          server: "helloServer",
          operator: "mike",
        },
      ],
    };
  },
  methods: {
    greet: function (event) {
      // `this` 在方法里指向当前 Vue 实例
      alert("Hello " + this.name + "!");
      // `event` 是原生 DOM 事件
      if (event) {
        alert(event.target.tagName);
      }
    },
    handleAdd: function () {
      this.tableData.push({
        entrance: this.dyeing.entrance,
        app: this.dyeing.app,
        server: this.dyeing.server,
        operator: "mike",
      });
    },
  },
};
</script>

<style>
.drawer-entrance {
  display: flex;
  margin-bottom: 10px;
}
.drawer-entrance .title {
  width: 80px;
  text-align: right;
  margin-right: 10px;
}
.btn {
  margin-left: 80%;
}

.dying-table {
  margin-top: 40px;
  margin-bottom: 40px;
}

.content {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  overflow-x: hidden;
}

.left{
    flex: 1;
    display: block;
    float: left;
    width: 80%;
}
.right {
  border: 1px solid #000;
  float: right;
  width: 25%;
  height: 600px;
  opacity: 100%;
  position: absolute;
  right:0;
  background-color: white;
}
.fade-enter-active {
    transition: right 0.8s;
}

.fade-leave-active {
    transition: right 0s;
}

.fade-enter, .fade-leve-to {
    right: -40%;
}
</style>