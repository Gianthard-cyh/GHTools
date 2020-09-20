<template>
  <div class="numbers" type="flex" justify="center">
    <a-row id="row" :gutter="16">
      <a-col class="gutter-row" :span="6" style="max-width:300px">
        <div class="gutter-box">
          <a-card title="脸黑榜">
            <a-table :columns="columns" :data-source="list" size="small"></a-table>
          </a-card>
        </div>
      </a-col>
      <a-col class="gutter-row" :span="18">
        <div class="gutter-box">
          <a-card id="right" title="抽取一名幸运观众" style=".ant-card-body:{text-align: center;}">
            <span style="height:500px;width:500px;font-size:300px;" class="num">{{num}}</span>
            <a-empty :hidden="flag" />
            <br />
            <a-button
              @click="btnclick"
              type="primary"
              style="min-height:50px;width:300px;font-size:23px;padding:5px"
            >下一个就是你~</a-button>
          </a-card>
        </div>
      </a-col>
    </a-row>
  </div>
</template>

<script>
import Vue from 'vue'
const columns = [
  {
    dataIndex: "key",
    key: "key",
    title: "学号",
  },
  {
    title: "被点名次数",
    dataIndex: "value",
    key: "value",
    sorter: (a, b) => a.value - b.value,
    defaultSortOrder: 'descend',
  },
];

export default {
  name: "numbers",
  data() {
    return {
      num: "",
      flag: false,
      list: [],
      columns,
    };
  },
  mounted: function () {
    console.log("created");
    this.list = new Array(56);
    this.list.fill();
    for (var i in this.list) {
      var j = { key: parseInt(i) + 1, value: 0 };
      this.list[i] = j;
    }
  },
  methods: {
    btnclick() {
      this.flag = true;
      this.num = Math.ceil(Math.random() * 56);
      for (var i in this.list) {
        if (this.list[i].key == this.num) {
          Vue.set(this.list,i,{key:this.list[i].key,value:this.list[i].value+1});
        }
      }
    },
  },
};
</script>

<style>
.numbers {
  height: 100%;
}
#row {
  height: 100%;
}
.gutter-row {
  height: 100%;
}
.gutter-box {
  min-height: 100%;
}
.ant-card {
  border-radius: 10px;
  border: 0px;
}
.num {
  user-select: none;
}
#right > .ant-card-body {
  text-align: center;
}
</style>