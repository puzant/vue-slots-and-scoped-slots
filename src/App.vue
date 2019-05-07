<template>
  <div id="app">
    <HelloWorld msg="VueJs frameWork" />
    <hello>
      <img slot="vuejs-image" width="25%" src="./assets/logo.png">

      <h2 slot="line1">hello there</h2>
      <hr slot="seperator">
      <h3 slot="line2">this is VueJs slots test</h3>

      <a href="" slot="link1">link1</a>
      <a href="" slot="link2">link2</a>
      <a href="" slot="link3">link3</a>


      <p slot="paragraph">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>

      <button class="btn" slot="btn" @click="greet()">Click me</button>
      <!-- accessing the scoped slot from the child -->
      <p slot-scope="defaultSlotText">{{defaultSlotText.text}}</p>

      <h2 slot="exmaple-title">another example with scoped slots</h2>

      <div slot="notificationData" slot-scope="props">
        <div class="notification-container" v-for="(item) in props.notifications">
          <p class="notification" :style=" { background: item.hexColor } ">{{item.name}}</p>
        </div>
      </div> 

    </hello>
  </div>
</template>

<script>
import Hello from "./components/Hello";
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    Hello,
    HelloWorld
  },
  methods: {
    greet() {
      alert("hello there,I am greeting you from the parent");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


.btn {
  border: 1px solid #fff;
  color: #fff;
  background-color: rgb(67, 145, 99);
  border-radius: 5px;
  padding: 5px;
}

.btn:focus {
  border: none;
  outline: none;
}

hr {
  width: 50%;
}

.notification-container {
  display: flex;
  justify-content: center;
}

.notification {
  margin: 7px;
  font-weight: bold;
  color: #111;
  padding: 4px;
  width: 30%;
  border-radius: 5px;
}

</style>
