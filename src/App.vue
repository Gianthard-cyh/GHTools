<template>
  <div id="app">
    <a-layout id="components-layout-demo-top-side-2">
      <a-layout-header class="header">
        <h1 style="color:white;font-size:30px;letter-spacing:-3px">GHTools</h1>
      </a-layout-header>
      <a-layout>
        <a-layout-sider width="200" style="background: #fff">
          <a-menu
            mode="inline"
            :style="{ height: '100%', borderRight: 1 }"
            :default-selected-keys="['1']"
          >
            <a-menu-item key="1">
              <a-icon type="number" />随机点名
            </a-menu-item>
          </a-menu>
        </a-layout-sider>
        <a-layout style="padding:25px">
          <numbers />
        </a-layout>
      </a-layout>
    </a-layout>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import numbers from "./components/numbers";

export default {
  name: "App",
  components: {
    HelloWorld,
    numbers,
  },
};
</script>

<style>
#app {
  height: 100%;
}
.ant-layout {
  min-height: 100%;
}
.my-card {
  border-radius: 24px;
  background: linear-gradient(225deg, #ffffff, #ffffff);
  box-shadow: -41px 41px 82px #aeaeae, 41px -41px 82px #ffffff;
}
</style>
