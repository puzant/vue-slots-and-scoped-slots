<template>
  <div id="app">
    <HelloWorld msg="VueJs frameWork" />
    <hello @passData="showE">

      <template slot="vuejs-image" slot-scope="props">
        <transition name="slex-fade">
          <img v-show="props.showImage" width="15%" src="./assets/logo.png">
        </transition>
        <br>
        <button @click="showHideDate()"> show / hide Date </button>
        <transition name="slex-fade">
          <p v-show="shouldShowDate">{{props.date}}</p>
        </transition>
      </template>
      

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
      <p slot="paragraph-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus error cum inventore atque asperiores blanditiis voluptatibus autem numquam illo doloribus? Voluptatum ipsa minima quo reiciendis magni adipisci repellendus laboriosam accusantium.</p>

      <div slot="notificationData" slot-scope="props">
        <div class="notification-container" v-for="(item) in props.notifications" :key="item.id">
          <p class="notification" :style=" { background: item.hexColor } ">{{item.name}}</p>
        </div>
      </div> 

      <div slot="namesData" slot-scope="props"> <!-- props is used to acces the child component data -->
        <div class="names-container" v-for="(name) in props.names" :key="name.id">
          <p class="names">{{name}}</p>
        </div>
      </div>

    </hello>

    <transition name="slex-fade">
      <hr v-show="showLine">
    </transition>

    <Tasks>
      <!-- custumized slots code here -->
      <template slot="tasks-header-title">
        <h1>These are the custumized slots</h1>
      </template>

      <template slot="task" slot-scope="props">
        <transition-group name="slex-fade">    
          <p 
            class="slot-task"
            v-for="(t, index) in props.tasks"
            :key="t.id"
            :style="{ backgroundColor: t.backgroundColor }">

            {{t.name}}
          </p>
        </transition-group>
        
      </template>
    </Tasks>

    <hr>

    <ImageGallery>
      <template slot="gallery">

        <h3>Winter is here</h3>
        <img src="./assets/pexels-photo-306825.jpeg" alt="">

      </template>
    </ImageGallery >

  </div>
</template>

<script>
import Hello from "./components/Hello";
import HelloWorld from "./components/HelloWorld";
import Tasks from "./components/Tasks"
import ImageGallery from "./components/ImageGallery"

export default {
  name: "App",
  data() {
    return {
      showLine: true,
      shouldShowDate: true,
      shouldShowDeleteBtn: false
    }
  },
  components: {
    Hello,
    HelloWorld,
    Tasks,
    ImageGallery
  },
  methods: {
    greet() {
      alert("hello there,I am greeting you from the parent");
    },

    showE(props) {
      console.log('passed from the child', props)
    },

    showHideDate() {
      if (this.shouldShowDate) return this.shouldShowDate = false
        return this.shouldShowDate = true
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

.slot-task {
  margin: 10px;
  display: inline-block;
  padding: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
  color: #111;
  font-weight: bold;
}

.delete-task {
  content: "X";
  margin-left: 20px;
  color: #fff;
}

img {
  border: 1px solid #ccc;
  border-radius: 5px;
  opacity: .7;
  transition: .2s;
}

img:hover {
  opacity: 1;
  cursor: pointer;
}

.slex-fade-enter-active, .slex-fade-leave-active {
  transition: opacity .5s;
}
.slex-fade-enter, .slex-fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
