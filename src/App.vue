<template>
  <div class="xxxglobal" id="xxxglobal">
    <div class="xxxnavbar">
      <img id="xxxprofileIcon" src="./assets/Icones/person.png" alt="Icone du profil">
      <hr>
      <img id="xxxplaylistIcon" src="./assets/Icones/playlist.png" alt="Icone de playlist">
      <img id="xxxeventIcon" src="./assets/Icones/event.png" alt="Icone de event">
      <img id="xxxgroupIcon" src="./assets/Icones/group.png" alt="Icone de group">
      <img id="xxxmoodIcon" src="./assets/Icones/mood.png" alt="Icone de mood">
    </div>

    <div class="xxxleftSide" id="xxxleftSide">
      <div class="xxxmyPlaylists" id="xxxmyPlaylists">
        <div id="xxxglobalTitle" @click="resize(1)">
          <span id="xxxmenuTitle">Mes playlists</span>
          <img id="xxxarrowDown" src="./assets/Icones/arrowDown.png" alt="Arrow down icon">
        </div>
        <div class="xxxplaylistContainer" id="xxxplaylistContainer">
          <div id="xxxsinglePlaylist" v-for="playlist in playlists">
            <img v-bind:src="playlist.img">
            <div id="xxxplaylistOverlay">
              <img id="xxxcheckIcon" src="./assets/Icones/check.png" alt="Check icon">
            </div>
            <div v-if="playlist.isRight == false" id="xxxplaylistDetailsRight" >
              {{playlist.name}}
            </div>
            <div v-if="playlist.isRight == true" id="xxxplaylistDetailsLeft">
              true
            </div>
          </div>
        </div>
        <div id="xxxgradientBack">
        </div>
      </div>

      <div class="xxxmyFriendsPlaylists" id="xxxmyPlaylists">
        <div id="xxxglobalTitle" @click="resize(2)">
          <span id="xxxmenuTitle">Playlists de mes amis</span>
          <img id="xxxarrowDown" src="./assets/Icones/arrowDown.png" alt="Arrow down icon">
        </div>
        <div class="xxxplaylistContainer" id="xxxfplaylistContainer">
          <div id="xxxsinglePlaylist" v-for="playlist in playlists">
            <img v-bind:src="playlist.img">
            <div id="xxxplaylistOverlay">
              <img id="xxxcheckIcon" src="./assets/Icones/check.png" alt="Check icon">
            </div>
            <div v-if="playlist.isRight == false" id="xxxplaylistDetailsRight" >
              {{playlist.name}}
            </div>
            <div v-if="playlist.isRight == true" id="xxxplaylistDetailsLeft">
              true
            </div>
          </div>
        </div>
        <div id="xxxgradientBack">
        </div>
      </div>
    </div>

    <!--<img src="./assets/line.png" id="draggableLine" @draggable="true" @dragstart="dragStart($event)" @dragover.prevent @drop="test($event)" @dragover.prevent @drag="move($event)">-->

    <div class="xxxrightSide" id="xxxrightSide">
      <div class="xxxmyEvents">
        <span id="xxxmenuTitle">Mes évènements</span><img id="xxxarrowDown" src="./assets/Icones/arrowDown.png" alt="Arrow down icon">
        <div class="xxxeventContainer">
          <div id="xxxsingleEvent" v-for="event in events">
            <img v-bind:src="event.img">
            <div id="xxxeventOverlay">
            </div>
          </div>
        </div>
      </div>
      <div class="xxxgroups">
      </div>
      <div class="xxxmoods">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      enabled_myPlaylists: true,
      enabled_myFriendsPlaylists: true,
      playlists: [
        {name: '0', img: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcQ8oSldZDiZkQkxqhUaixRmbCHUHieUf5Tvn25WqyxuO6A97ssJ'},
        {name: '1', img: 'https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTgz6hZmEOKhFtTyksQ8YO-zYyJKIxgslNsJc0kOg1nZXLn9LTu'},  
        {name: '2', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQuix2_4M4wJW5WPulr4Jiv3m6H6nJwXL-4FZAF0ixMijcr-a3U'}, 
        {name: '3', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTvrjhfN_GWaK4E1dOrsQ4bTFpOHWTpT2UqCO3tixJQyph1r2rl'}, 
        {name: '4', img: 'https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcQxVolTA5obssR6TBbdXs-DqgPFddWZCh2KSSbXBFUatj3A2gf_6Q'}, 
        {name: '5', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSDOOB9RK2hfXdA9pd3ivlHfTILdQU3AjBMOo6RNI8mgQ0N0sHi'}, 
        {name: '6', img: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcT-b_KEtBRBuPBIsQCkdxpF7Xy6V0-BSY71zeoDwyB_rYgZOo1x'}, 
        {name: '7', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSHRNtaLNKcGsxW0N7PDXIJVuI92ywdB3SVAQVkO_s4OcoXNT2a'}, 
        {name: '8', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSe9NcDacC3OZjhN02x5kNL-Qevv-3fHhBIU7_3bowaQTa_Ia28'}, 
        {name: '9', img: 'http://loudwire.com/files/2011/11/Nirvana-Kitten-Album-Cover.jpg'},
        {name: '10', img: 'https://s-media-cache-ak0.pinimg.com/originals/50/f4/d5/50f4d510a9c309d587c3108606ae8ac1.jpg'},
        {name: '11', img: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcRhh4LKCVmSZS3GsdKp065AnZjk6pwRpSyP8RjA3rokYDTZ4Bly'},
        {name: '12', img: 'https://s-media-cache-ak0.pinimg.com/736x/28/3e/8d/283e8d5f7263e56bee957a9ddb3f336d--cd-design-album-cover-design.jpg'}  
      ],
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
    checkPlaylistPosition() {
      this.playlists = this.playlists.map(p => { p.isRight = false; return p })
      var playlistSize = document.getElementById('xxxsinglePlaylist').offsetWidth + 20;
      var containerSize = document.getElementById('xxxmyPlaylists').offsetWidth -20;
      var count = 0;
      for(var i = 0; i<this.playlists.length; i++) {
        var index = this.playlists.indexOf(this.playlists[i]);
        count += playlistSize;
        if(count > containerSize) {
          this.playlists[i-1].isRight = true;
          count = playlistSize;
        }
      }
    },
    async resize(_case) {
      debugger;
      switch(_case) {
        case 1:
        {
          if(this.enabled_myPlaylists) 
          {
            if(this.enabled_myFriendsPlaylists)
            {
              document.getElementById('xxxplaylistContainer').style.height = '0vh';
              document.getElementById('xxxfplaylistContainer').style.height = 'auto';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '0px';
              document.getElementById('xxxgradientBack').style.display = 'none';
              this.enabled_myPlaylists = false;
            } else {
              document.getElementById('xxxplaylistContainer').style.height = '0vh';
              document.getElementById('xxxfplaylistContainer').style.height = '0vh';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '0px';
              document.getElementById('xxxgradientBack').style.display = 'initial';
              this.enabled_myPlaylists = false;
            }
          } else if(!this.enabled_myPlaylists) 
          {
            if(this.enabled_myFriendsPlaylists)
            {
              document.getElementById('xxxplaylistContainer').style.height = '42vh';
              document.getElementById('xxxfplaylistContainer').style.height = '42vh';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '30px';
              document.getElementById('xxxgradientBack').style.display = 'initial';
              this.enabled_myPlaylists = true;
            } else {
              document.getElementById('xxxplaylistContainer').style.height = 'auto';
              document.getElementById('xxxfplaylistContainer').style.height = '0vh';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '0px';
              document.getElementById('xxxgradientBack').style.display = 'none';
              this.enabled_myPlaylists = true;
            }
          }
        } break;
        case 2:
        {
          if(this.enabled_myFriendsPlaylists) 
          {
            if(this.enabled_myPlaylists)
            {
              await (document.getElementById('xxxfplaylistContainer').style.height = '0vh');
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '0px';
              document.getElementById('xxxgradientBack').style.display = 'none';
              document.getElementById('xxxplaylistContainer').style.height = 'auto';
              this.enabled_myFriendsPlaylists = false;
            } else {
              document.getElementById('xxxplaylistContainer').style.height = '0vh';
              document.getElementById('xxxfplaylistContainer').style.height = '0vh';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '0px';
              document.getElementById('xxxgradientBack').style.display = 'initial';
              this.enabled_myFriendsPlaylists = false;
            }
          } else if(!this.enabled_myFriendsPlaylistsPlaylists) 
          {
            if(this.enabled_myPlaylists)
            {
              document.getElementById('xxxplaylistContainer').style.height = '42vh';
              document.getElementById('xxxfplaylistContainer').style.height = '42vh';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '30px';
              document.getElementById('xxxgradientBack').style.display = 'initial';
              this.enabled_myFriendsPlaylists = true;
            } else {
              document.getElementById('xxxfplaylistContainer').style.height = 'auto';
              document.getElementById('xxxplaylistContainer').style.height = '0vh';
              document.getElementById('xxxmyPlaylists').style.paddingBottom = '0px';
              document.getElementById('xxxgradientBack').style.display = 'none';
              this.enabled_myFriendsPlaylists = true;
            }
          }
        } break;
        case 3:
        {

        } break;
        case 4:
        {

        } break;
      }
    },
    move(e) {
      console.log('MOVE METHOD');
      var bar = document.getElementById('draggableLine');
      var one = document.getElementById('xxxleftSide');
      var two = document.getElementById('xxxrightSide');
      bar.style.left = (e.x)-4+"px";
      one.style.width = (e.x - 100)+"px";
      two.style.width = document.getElementById('xxxglobal').offsetWidth - (e.x)+4+"px";
      console.log(e.x)
    },
    dragStart(e) {
      this.dragStartPos = e.x;
      console.log("DRAG START POS " + this.dragStartPos);
    }
  },
  mounted() {
    this.playlists = this.playlists.map(p => { p.isRight = false; return p })
    this.$nextTick(function() {
      window.addEventListener('resize', this.checkPlaylistPosition);
    })
    this.checkPlaylistPosition();
  }
}

</script>

<style lang="less" src="./styles/app.less">
</style>
