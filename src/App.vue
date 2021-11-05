<template>
  <div id="app">
    <div class="office">
      <Map @tableClicked="tableClicked" @mapClicked="mapClicked" />
      <SideMenu
        v-bind:isUserOpenned.sync="isUserOpenned"
        :choosenUserId="choosenUserId"
      />
    </div>
  </div>
</template>

<script>
import Map from "./components/Map.vue";
import SideMenu from "./components/SideMenu.vue";

export default {
  name: "App",
  data() {
    return {
      isUserOpenned: false,
      choosenUserId: null,
    };
  },
  components: {
    Map,
    SideMenu,
  },
  methods: {
    tableClicked(id) {
      // После эммита id приводится к строке? Хотя когда получаю значение из html оно является числом
      this.choosenUserId = Number(id);
      this.isUserOpenned = true;
    },
    mapClicked() {
      this.isUserOpenned = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;
  background-color: #fafafa;
  padding: 24px;
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
}

* {
  box-sizing: border-box;
}

h3 {
  margin-top: 0;
}

.office {
  display: grid;
  grid-template-columns: 1fr 320px;
  border-radius: 6px;
  border: 1px solid #ccd8e4;
  height: 100%;
  background: white;
  max-width: 1500px;
  margin: 0 auto;
}
</style>
