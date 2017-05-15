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
        <span id="xxxmenuTitle">Mes playlists</span>
        <div class="xxxplaylistContainer">
          <div id="xxxsinglePlaylist" v-for="playlist in playlists">
            <img v-bind:src="playlist.img">
            <div id="xxxplaylistOverlay">
              <img id="xxxcheckIcon" src="./assets/Icones/check.png" alt="Check icon">
            </div>
            <div id="xxxplaylistDetails">
              {{playlist.name}}
            </div>
          </div>
        </div>
        <div id="xxxgradientBack">
        </div>
      </div>

      <div class="xxxmyFriendsPlaylists">
        <span id="xxxmenuTitle">Mes playlists</span>
        <div class="xxxplaylistContainer">
          <div id="xxxsinglePlaylist" v-for="playlist in playlists">
            <img v-bind:src="playlist.img">
          </div>
        </div>
        <div id="xxxgradientBack">
        </div>
      </div>
    </div>

    <img src="./assets/line.png" id="draggableLine" @draggable="true" @dragstart="dragStart($event)" @dragover.prevent @drop="test($event)" @dragover.prevent @drag="move($event)">

    <div class="xxxrightSide" id="xxxrightSide">
      <p>{{playlists}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      playlists: [
        {name: '1111111111111', img: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcQ8oSldZDiZkQkxqhUaixRmbCHUHieUf5Tvn25WqyxuO6A97ssJ'},
        {name: '1', img: 'https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcTgz6hZmEOKhFtTyksQ8YO-zYyJKIxgslNsJc0kOg1nZXLn9LTu'},  
        {name: '1', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQuix2_4M4wJW5WPulr4Jiv3m6H6nJwXL-4FZAF0ixMijcr-a3U'}, 
        {name: '1', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTvrjhfN_GWaK4E1dOrsQ4bTFpOHWTpT2UqCO3tixJQyph1r2rl'}, 
        {name: '1', img: 'https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcQxVolTA5obssR6TBbdXs-DqgPFddWZCh2KSSbXBFUatj3A2gf_6Q'}, 
        {name: '1', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSDOOB9RK2hfXdA9pd3ivlHfTILdQU3AjBMOo6RNI8mgQ0N0sHi'}, 
        {name: '1', img: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcT-b_KEtBRBuPBIsQCkdxpF7Xy6V0-BSY71zeoDwyB_rYgZOo1x'}, 
        {name: '1', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSHRNtaLNKcGsxW0N7PDXIJVuI92ywdB3SVAQVkO_s4OcoXNT2a'}, 
        {name: '1', img: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSe9NcDacC3OZjhN02x5kNL-Qevv-3fHhBIU7_3bowaQTa_Ia28'}, 
        {name: '1', img: 'http://loudwire.com/files/2011/11/Nirvana-Kitten-Album-Cover.jpg'},
        {name: '1', img: 'https://s-media-cache-ak0.pinimg.com/originals/50/f4/d5/50f4d510a9c309d587c3108606ae8ac1.jpg'},
        {name: '1', img: 'https://encrypted-tbn2.gstatic.com/images?q=tbn:ANd9GcRhh4LKCVmSZS3GsdKp065AnZjk6pwRpSyP8RjA3rokYDTZ4Bly'},
        {name: '1', img: 'https://s-media-cache-ak0.pinimg.com/736x/28/3e/8d/283e8d5f7263e56bee957a9ddb3f336d--cd-design-album-cover-design.jpg'}  
      ]
    }
  },
  methods: {
    checkPlaylistPosition() {
      var playlistSize = document.getElementById('xxxsinglePlaylist').offsetWidth + 20;
      var containerSize = document.getElementById('xxxmyPlaylists').offsetWidth;
      var count = 0;
      console.log(containerSize, playlistSize);
      for(var i = 0; i<this.playlists.length; i++) {
        var index = this.playlists.indexOf(this.playlists[i]);
        count += playlistSize;
        if(count > containerSize) {
          this.playlists[i].isRight = true;
          count = 0;
        }
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
    this.$nextTick(function() {
      window.addEventListener('resize', this.checkPlaylistPosition);
    })
  }
}

</script>

<style lang="less" src="./styles/app.less">
</style>
