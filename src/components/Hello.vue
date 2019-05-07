<template>
  <div class="hello">
    <!-- add the image here as slot -->
    <slot name="vuejs-image"></slot>
    <slot name="line1"></slot>
    <slot name="seperator"></slot>
    <slot name="line2"></slot>

    <slot name="link1"></slot>
    <slot name="link2"></slot>
    <slot name="link3"></slot>

    <slot name="paragraph"></slot>
    <slot name="btn"></slot>
    <!-- scoped slot -->
    <slot :text="defaultSlotText"></slot>

    <ul v-for="s in shapes">
      <li :style=" { background: s.hex } " @click="tellMeShapeWithColor(s)">{{s.name}}, {{s.sides}}, {{s.hex}}</li>
    </ul>

    <slot name="exmaple-title"></slot>
    
    <slot name="notificationData" :notifications="notifications"></slot>

  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      defaultSlotText: "I'll get rendered inside the default slot!.",
      infoMessage: "hello there this is info message",
      shapes: [
        { name: "Square", sides: 4, hex: "#F4D03F", colorName: 'Saffron' },
        { name: "Hexagon", sides: 6, hex: "#229954", colorName: 'Eucalyptus'},
        { name: "Triangle", sides: 3, hex: "#9B59B6", colorName: 'Wisteria' }
      ],
      notifications: [
        {name: 'warning', hexColor: '#FA3E3E'},
        {name: 'info', hexColor: '#005EB2'},
        {name: 'error', hexColor: '#FFCA00'},
      ]
    };
  },

  methods: {
    tellMeShapeWithColor(s) {
      alert('shape is ' + s.name + '\n' + 'color is ' + this.findTheColorName(s))
    },

    findTheColorName(s) {
     return s.colorName
    }

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 20px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
  margin: 20px;
}

li {
  color: #111;
  padding: 4px;
  border-radius: 5px;
  width: 30%;
  font-weight: bold;

}
</style>
