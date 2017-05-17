<template>
  <div id="app">
    
    <div class="xxxmyEvents">
      <span id="xxxmenuTitle">Mes évènements</span>
      <div class="xxxeventContainer">
        <transition-group name="list" tag="div">
          <div id="xxxsingleEvent" v-for="event in events" v-bind:key="event" @click="setFirst(event)">
            <img v-bind:src="event.img">
          </div>
        </transition-group>
      </div>
    </div>

    <div class="xxxgroups">
      <div id="list-demo">
        <button v-on:click="add">Add</button>
        <button v-on:click="remove">Remove</button>
        <transition-group name="list" tag="p">
          <span v-for="item in items" v-bind:key="item" class="list-item">
            {{ item }}
          </span>
        </transition-group>
      </div>
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
      
  items: [1,2,3,4,5,6,7,8,9],
  nextNum: 10,
      events: [
        {name: 'ACDC TRIBUTE', img: 'http://www.event-yours.fr/wp-content/uploads/2017/04/EVENT-YOURS_EVENTS-PLANNER.jpg'},
        {name: 'ACDC TRIBUTE', img: 'https://cdn.evbuc.com/images/25935758/32755652699/1/logo.jpg'},
        {name: 'ACDC TRIBUTE', img: 'http://www.sortiedenullepart.be/wp-content/uploads/2017/05/rsz_john-price-278681-400x200.jpg'},
        {name: 'ACDC TRIBUTE', img: 'http://www.apptus.com/wp-content/uploads/2016/02/connect-main-theatre.jpg'},
        {name: 'ACDC TRIBUTE', img: 'http://paintnpartyevents.com/wp-content/uploads/2017/03/MAY-8-Spring-Love-400x200.jpg'},
        {name: 'ACDC TRIBUTE', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTNtb-U01S7XJrvWvIVawrHOxW_pBNnmFWX1FYh-ttXxQqZs9svsw'}
      ]
    }
  },
  methods: {
    randomIndex: function () {
      return Math.floor(Math.random() * this.items.length)
    },
    add: function () {
      this.items.splice(this.randomIndex(), 0, this.nextNum++)
    },
    remove: function () {
      this.items.splice(this.randomIndex(), 1)
    },
    setFirst(event) {
      var tmp = this.events.indexOf(event);
      this.events.splice(tmp, 1);
      this.events.splice(2, 0, event);
    }
  }   
}

</script>

<style lang="less" src="./styles/event.less">
</style>
