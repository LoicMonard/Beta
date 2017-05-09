<template>
  <div id="app">
    <div id="all">
      <div id="one">
        <transition-group name="mMove" tag="div">
          <div id="playlist" v-for="div in divs" v-bind:key="div">
            {{div}}
          </div>
        </transition-group>
      </div>
      <div id="two">
        <button @click="shuffle()">Shuffle</button>
      </div>
    </div>
    <div id="p1" @draggable="true" @dragstart="dragStart($event)" @dragover.prevent @drop="test($event)" @dragover.prevent @drag="move($event)"><img src="./assets/transparentLine.png"></div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      dragStartPos: '',
      divs: [1, 2, 3, 4, 5, 6]
    }
  },
  methods: {
    test(e) {
      var t = document.getElementById('p1');
      t.style.left = e.x-5 +"px";
      console.log(e);
      if(e.x-5 < 200)
        t.style.left = 200+"px";
    },
    move(e) {
      console.log('MOVE METHOD');
      var bar = document.getElementById('p1');
      var one = document.getElementById('one');
      var two = document.getElementById('two');
      bar.style.left = (e.x - 5)+"px";
      one.style.width = (e.x - 5)+"px";
      two.style.width = document.getElementById('all').offsetWidth - (e.x - 5)+"px";
      console.log(e.x)
    },
    dragStart(e) {
      this.dragStartPos = e.x;
      console.log("DRAG START POS " + this.dragStartPos);
    },
    shuffle() {
      this.divs.push(0);
    }
  }
}

</script>

<style>
#all {
  width: 100%;
}
  
#one {
  width: 50%;
  min-width: 200px;
  background: red;
  float: left;
  text-overflow: ellipsis;
}

#playlist {
  width: 200px;
  height: 200px;
  display: inline-block;
  border: 2px solid green;
  transition: all .3s;
  -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
  -moz-box-sizing: border-box;    /* Firefox, other Gecko */
  box-sizing: border-box; 
  padding: 10px;
}

#two {
  width: 50%;
  background: yellow;
  float: left;
}

#p1 {
  border: 1px solid green;
  position: absolute;
  top: 0px;
  left: 500px;
}

.mMove-move {
  transition: transform 1s;
}

.mMove-enter-active, .mMove-leave-active {
  transition: opacity .5s, transform .5s;
}

.mMove-enter, .mMove-leave-active {
  opacity: 0;
  transform: translateY(-200px);
}
</style>
