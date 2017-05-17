<template>
  <div id="app">
    
    <div class="xxxmyEvents">
      <span id="xxxmenuTitle">Mes évènements</span>
      <div class="xxxeventContainer">
        <div id="xxxsingleEvent" v-for="event in events">
          <img v-bind:src="event.img">
        </div>
      </div>
    </div>

    <div class="xxxgroups">
    </div>

    <div class="xxxmoods">
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      events: [
        {name: 'ACDC TRIBUTE', img: 'https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F27583588%2F181475566476%2F1%2Foriginal.jpg?h=200&w=450&rect=0%2C0%2C9000%2C4500&s=1dc5f64eab7c977380614b4bd97d6183'},
        {name: 'ACDC TRIBUTE', img: 'https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F27583588%2F181475566476%2F1%2Foriginal.jpg?h=200&w=450&rect=0%2C0%2C9000%2C4500&s=1dc5f64eab7c977380614b4bd97d6183'},
        {name: 'ACDC TRIBUTE', img: 'https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F27583588%2F181475566476%2F1%2Foriginal.jpg?h=200&w=450&rect=0%2C0%2C9000%2C4500&s=1dc5f64eab7c977380614b4bd97d6183'},
        {name: 'ACDC TRIBUTE', img: 'https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F27583588%2F181475566476%2F1%2Foriginal.jpg?h=200&w=450&rect=0%2C0%2C9000%2C4500&s=1dc5f64eab7c977380614b4bd97d6183'},
        {name: 'ACDC TRIBUTE', img: 'https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F27583588%2F181475566476%2F1%2Foriginal.jpg?h=200&w=450&rect=0%2C0%2C9000%2C4500&s=1dc5f64eab7c977380614b4bd97d6183'},
        {name: 'ACDC TRIBUTE', img: 'https://img.evbuc.com/https%3A%2F%2Fcdn.evbuc.com%2Fimages%2F27583588%2F181475566476%2F1%2Foriginal.jpg?h=200&w=450&rect=0%2C0%2C9000%2C4500&s=1dc5f64eab7c977380614b4bd97d6183'}
      ]
    }
  },
  methods: {
  }   
}

</script>

<style lang="less" src="./styles/event.less">
</style>
