<template>
  <div class="pd-top-50 pd-bottom-50">
    <MyHeader />
    <div class="myheadercontain">
      <div class="tab-tilte">
        <!-- <div @click="tabChange(0,child1)"
             v-bind:class="{ tabactivate:0==current}">My Votes</div>
        <div @click="tabChange(1,child2)"
             v-bind:class="{ tabactivate:1==current}">My Medal</div> -->
        <div @click="tabChange(2, child3)"
             v-bind:class="{ tabactivate: 2 == current }">
          My Earnings
        </div>
      </div>
      <div :is="currentView"></div>
    </div>
  </div>
</template>
<script>
import MyHeader from "./myheader";
// import child1 from "./myvote";
// import child2 from "./mymedal";
import child3 from "./myearnings";
export default {
  name: "Mine",
  async created () {
    console.log(this.$checkLogin())
    if (!this.$checkLogin()) {
      this.$router.push("/login");
    }
  },
  data () {
    return {
      current: 0,
      // child1: "child1",
      // child2: "child2",
      child3: "child3",
      currentView: "child3", // 默认选中第一项
    };
  },
  methods: {
    tabChange (index, tabItem) {
      this.current = index;
      this.currentView = tabItem;
      var el = event.currentTarget;
    },
  },
  components: {
    // child1,
    // child2,
    child3,
    MyHeader
  },
};
</script>
<style scoped>
.tabactivate {
  color: #2175bc;
  border-bottom: thick solid #2175bc;
}

.myheadercontain {
  margin: auto;
  text-align: center;
}

.tab-tilte {
  display: flex;
  width: 80%;
  margin: 1em auto;
  text-align: center;
  font-size: 2em;
  font-weight: 800;
}

.tab-tilte div {
  float: left;
  flex: 1;
  padding: 10px 0;
  text-align: center;
  cursor: pointer;
}

.tab-tilte .active {
  background-color: #09f;
  color: #3c7aef;
}

.tab-content div {
  float: left;
  width: 25%;
  line-height: 100px;
  text-align: center;
}

@media only screen and (max-width: 479px) {
  .tab-tilte {
    font-size: 1em;
    width: 100%;
  }
}
</style>