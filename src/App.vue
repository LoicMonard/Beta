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
      <div class="xxxmyPlaylists">
        <span id="xxxmenuTitle">Mes playlists</span>
        <div class="xxxplaylistContainer">
          <div id="xxxsinglePlaylist" v-for="playlist in playlists">
            <img v-bind:src="playlist.img">
          </div>
        </div>
      </div>
      <div class="xxxmyFriendsPlaylists">
        <span id="xxxmenuTitle">Playlists de mes amis</span>
      </div>
    </div>

    <img src="./assets/line.png" id="draggableLine" @draggable="true" @dragstart="dragStart($event)" @dragover.prevent @drop="test($event)" @dragover.prevent @drag="move($event)">

    <div class="xxxrightSide" id="xxxrightSide">
      <p>Hey</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      playlists: [
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'},
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'},  
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'}, 
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'},
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'},
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'},
        {name: '1', img: 'https://4.bp.blogspot.com/-Qls0bKPYaBY/WBdlpnE1vBI/AAAAAAAAid0/KI3fl-7x270i2Ywcr_2DmimhJp2PoljEgCLcB/s1600/Playlist-91coverart.jpg'}  
      ]
    }
  },
  methods: {
    move(e) {
      console.log('MOVE METHOD');
      var bar = document.getElementById('draggableLine');
      var one = document.getElementById('xxxleftSide');
      var two = document.getElementById('xxxrightSide');
      bar.style.left = (e.x)+"px";
      one.style.width = (e.x - 70)+"px";
      two.style.width = document.getElementById('xxxglobal').offsetWidth - (e.x)+"px";
      console.log(e.x)
    },
    dragStart(e) {
      this.dragStartPos = e.x;
      console.log("DRAG START POS " + this.dragStartPos);
    }
  }
}

</script>

<style lang="less" src="./styles/app.less">
</style>
