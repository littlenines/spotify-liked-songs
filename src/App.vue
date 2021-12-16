<template>
  <v-app>
    <div class="grid-wrap">
      <v-card height="100%" width="256" dark>
        <v-navigation-drawer permanent>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="text-h6">
                <v-icon>mdi-dots-horizontal</v-icon>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>

          <v-list dense nav dark>
            <v-list-item-group v-model="selectedItem">
              <v-list-item
                v-for="item in items"
                :key="item.title"
                link
                class="hov"
              >
                <v-list-item-icon>
                  <v-icon color="rgb(179, 179, 179)">{{ item.icon }}</v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title>{{ item.title }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>

              <v-list flat dark>
                <v-list-item v-for="item2 in items2" :key="item2.title" link>
                  <v-list-item-icon>
                    <v-icon color="rgb(179, 179, 179)">{{ item2.icon }}</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>{{ item2.title }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
              <v-divider></v-divider>
              <v-list flat dark>
                <v-list-item v-for="item3 in items3" :key="item3.title" link>
                  <v-list-item-content>
                    <v-list-item-title>{{ item3.title }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-list-item-group>
          </v-list>
        </v-navigation-drawer>
      </v-card>
      <v-main>
        <div class="target" id="scroll-target">
        <v-app-bar flat v-scroll:#scroll-target="onScroll" :color="color">
          <v-btn class="mx-2" fab dark x-small>
            <v-icon dark> mdi-chevron-left </v-icon>
          </v-btn>
          <v-btn class="mr-2" fab dark x-small>
            <v-icon dark> mdi-chevron-right </v-icon>
          </v-btn>
          <v-toolbar-title class="white--text text-h5 font-weight-black">
            <v-avatar color="green" class="ml-1 mr-3" size="44">
              <v-icon dark> mdi-play </v-icon> </v-avatar
            >Liked Songs</v-toolbar-title
          >

          <v-spacer></v-spacer>

          <v-chip pill dark color="black">
            <v-avatar left>
              <v-img src="blank.png"></v-img>
            </v-avatar>
            Littlezz
            <v-icon>mdi-menu-down</v-icon>
          </v-chip>
        </v-app-bar>

        <v-card class="like-color py-5 change-position">
          <v-list class="like-color">
            <v-list-item>
              <v-img
                src="liked.png"
                max-height="300"
                max-width="230"
                class="img-shadow ml-5"
              ></v-img>
              <v-list-item-content class="ml-5">
                <v-list-item-title class="white--text text-subtitle-1"
                  >PLAYLIST</v-list-item-title
                >

                <v-list-item-subtitle
                  class="white--text text-h1 font-weight-black"
                  >Liked Songs</v-list-item-subtitle
                >

                <v-list-item-subtitle class="text-subtitle-2 grey--text"
                  ><v-avatar size="25" class="mr-1">
                    <v-img src="blank.png"></v-img> </v-avatar
                  ><span class="white--text">Littlezz</span> • 10
                  Songs</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-card>

        <v-row id="row-margin">
          <v-avatar color="green" class="ml-5" size="60">
            <v-icon large dark> mdi-play </v-icon>
          </v-avatar>
          <v-icon class="ml-5 icon-hov" large
            >mdi-arrow-down-thin-circle-outline</v-icon
          >
          <v-spacer></v-spacer>
          <v-btn icon color="grey">
            <v-icon>mdi-magnify</v-icon>
          </v-btn>
          <p class="white--text mx-5 mt-1">
            Custom order <v-icon color="white">mdi-menu-down</v-icon>
          </p>
        </v-row>
      <v-container grid-list-xs>
        <ul class="nav-table white--text">
          <v-simple-table dark>
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-left" width="80px">#</th>
                  <th class="text-left">Title</th>
                  <th class="text-center" colspan="2">Album</th>
                  <th class="text-center" width="120px">Date Added</th>
                  <th class="text-center" width="70px">
                    <v-icon small>mdi-clock</v-icon>
                  </th>
                </tr>
              </thead>
            </template>
          </v-simple-table>
        </ul>
      
       
          <v-simple-table dark>
            <template v-slot:default>
              <tbody>
                <tr v-for="item in songs" :key="item.id">
                  <td>{{ item.id }}</td>
                  <td>
                    
                      <v-list-item>
                        <v-avatar tile class="mr-2" size="40">
                          <img :src="item.thumb" alt="picture" />
                        </v-avatar>

                        <v-list-item-content>
                          <v-list-item-title
                            v-html="item.name"
                          ></v-list-item-title>
                          <v-list-item-subtitle
                            v-html="item.created_by"
                          ></v-list-item-subtitle>
                        </v-list-item-content>
                      </v-list-item>
                    
                  </td>
                  <td>{{ item.name }}</td>
                  <td>4 hours ago</td>
                  <td>{{ item.duration }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
           </v-container>
        </div>
      </v-main>

      <v-card class="mx-auto" width="270" max-width="500" dark>
        <v-navigation-drawer absolute permanent right>
          <v-system-bar color="transparent" dark>
            <v-spacer></v-spacer>
            <v-icon small class="hover-minus-copy">mdi-minus</v-icon>
            <v-icon class="hover-minus-copy" small>mdi-content-copy</v-icon>
            <v-icon class="hover-close" small>mdi-close</v-icon>
          </v-system-bar>
          <v-list>
            <v-subheader
              ><span class="white--text">Friend activity</span>
              <v-spacer></v-spacer
              ><v-icon small class="icon-hov"
                >mdi-account-plus-outline</v-icon
              ></v-subheader
            >
            <v-list-item v-for="chat in recent" :key="chat.title">
              <v-list-item-avatar>
                <v-img :alt="`${chat.title} avatar`" :src="chat.avatar"></v-img>
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title v-text="chat.title"></v-list-item-title>
                <v-list-item-subtitle
                  v-text="chat.headline"
                ></v-list-item-subtitle>

                <v-list-item-subtitle
                  v-text="chat.subtitle"
                ></v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-navigation-drawer>
      </v-card>
    </div>
    <v-footer dark padless height="90px">
      <div class="footer-playing">
        <img src="years.png" alt="years" class="footer-img" />
        <ul>
          <li class="title-text">Years Ago</li>
          <li class="grey--text sub-text">Kurt Stewart, Lomme</li>
        </ul>
        <v-icon small color="green">mdi-heart</v-icon>
      </div>

      <div class="footer-wrap mx-auto">
        <div class="mx-auto footer-icons">
          <v-icon small color="grey">mdi-shuffle-variant</v-icon>
          <v-icon color="grey">mdi-skip-previous</v-icon>
          <v-icon large>mdi-play-circle</v-icon>
          <v-icon color="grey">mdi-skip-next</v-icon>
          <v-icon color="grey">mdi-repeat-variant</v-icon>
        </div>

        <div class="footer-progress">
          <p class="mr-1">00:00</p>
          <v-progress-linear
            style="width: 500px"
            background-color="grey darken-1"
            color="grey lighten-1"
            value="15"
          ></v-progress-linear>
          <p class="ml-1">02:48</p>
        </div>
      </div>

      <div class="footer-sound mr-3">
        <v-icon color="grey">mdi-playlist-play</v-icon>
        <v-icon color="grey" class="mx-2">mdi-desktop-tower-monitor</v-icon>
        <v-icon color="grey">mdi-volume-high</v-icon>
        <v-progress-linear
          style="width: 100px"
          background-color="grey darken-1"
          color="grey lighten-1"
          value="15"
          class="mx-2"
        ></v-progress-linear>
        <v-icon color="grey">mdi-fullscreen</v-icon>
      </div>
    </v-footer>
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
       songs: null,
      selectedItem: 1,
      color: "transparent",
      items: [
        { title: "Home", icon: "mdi-home" },
        { title: "Search", icon: "mdi-magnify" },
        { title: "Your Library", icon: "mdi-bookshelf" },
      ],
      items2: [
        { title: "Create Playlist", icon: "mdi-plus-box" },
        { title: "Liked Songs", icon: "mdi-heart" },
      ],
      items3: [
        { title: "lofi hip hop music - beats to relax and study" },
        { title: "Programming" },
        { title: "Are you LoFi today?" },
        { title: "Faith Marie" },
        { title: "Linkin Park" },
      ],
      recent: [
        {
          avatar: "blank.png",
          title: "PiggSheriff",
          action: "3 d",
          headline: "Slowdance l•The Murder Capital",
          subtitle: `♫ Discover Weekly`,
        },
        {
          avatar: "blank.png",
          title: "Space",
          action: "4 d",
          headline: "When Angels Fall•Beyond The Black",
          subtitle: `♫ Songs Of Love And Death`,
        },
      ],
      previous: [
        {
          title: "Travis Howard",
          avatar: "https://cdn.vuetifyjs.com/images/lists/5.jpg",
        },
      ],
      // songs: [
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      //   {
      //     ID: 9,
      //     picture: "raimu.png",
      //     name: "The Girl I Haven't Met",
      //     artist: "Kudasaibeats",
      //     album: "Falling",
      //     date: "Nov 2, 2021",
      //     calories: "3:49",
      //   },
      // ],
      icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
      right: null,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);

    axios.get("http://orangevalleycaa.org/api/music/order/id")
    .then(response => (this.songs = response.data))
    .catch(error => console.log(error));
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll(e) {
      // When the window is scrolled
      // this.color =
      //   e.target.documentElement.scrollTop === 0 ? "red" : "white";
      if (e.target.scrollTop >= 300) {
        this.color = "deep-purple darken-4";
      } else {
        this.color = "transparent";
        document.querySelector(".v-toolbar__title").style.display = "none";
      }

      if (e.target.scrollTop >= 400) {
        document.querySelector(".v-toolbar__title").style.display = "inline";
      } else {
        document.querySelector(".v-toolbar__title").style.display = "none";
      }
    },
  },
};
</script>

<style>
.v-navigation-drawer__content {
  background-color: rgb(0, 0, 0) !important;
}

.hov {
  color: #fff !important;
}

.v-sheet.v-card {
  border-radius: 0px !important;
}

.grid-wrap {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.v-toolbar__title {
  display: none;
}
.hover-minus-copy:hover {
  background-color: grey;
}

.hover-close:hover {
  background-color: red;
}

.v-system-bar .v-icon {
  padding: 10px !important;
  margin: 0px !important;
}

.change-position {
  top: -64px !important;
}

.change-position .v-list {
  margin-top: 50px !important;
}

.like-color {
  background-color: rgba(73, 52, 142) !important;
}

.img-shadow {
  box-shadow: 0px 0px 50px 3px rgba(0, 0, 0, 0.65);
}

.v-card {
  box-shadow: none !important;
}

.v-main {
  width: 100wh;
  height: calc(100vh - 90px) !important;
  flex: auto !important;
  /* background: linear-gradient(
    0deg,
    rgba(2, 0, 36, 1) 40%,
    rgba(73, 52, 142, 1) 100%
  ) !important; */
  background-color: rgb(24, 24, 24) !important;
}

.target {
  height:calc(100vh - 90px);
  overflow:auto;
}

.row {
  position: relative !important;
  top: -43px !important;
}

#row-margin {
  margin-bottom: -27px !important;
}

.nav-table {
  list-style-type: none !important;
  margin: 0 !important;
  padding: 0 !important;
  overflow: hidden !important;
  position: -webkit-sticky; /* Safari */
  position: sticky !important;
  top: 63px !important;
}
.v-data-table {
  border-radius: none !important;
  background-color: transparent !important;
  color: #fff !important;
}

.thead-color {
  color: #fff !important;
}

.v-card .v-navigation-drawer {
  width: 270px !important;
}

.v-app-bar {
  position: sticky !important;
  top: 0 !important;
  z-index: 1 !important;
  background-color: transparent !important;
}

.row {
  margin: 0 !important;
}

.icon-hov {
  color: grey !important;
}

.icon-hov:hover {
  color: #fff !important;
}

.v-footer {
  background-color: rgb(24, 24, 24) !important;
  border-top: 1px solid rgb(40, 40, 40) !important;
}

.footer-playing {
  display: flex;
  align-items: center;
}

.footer-img {
  max-height: 55px;
  max-width: 55px;
  margin-left: 15px;
}

.footer-playing ul {
  padding-left: 10px !important;
}

.footer-playing ul li {
  text-decoration: none;
  list-style-type: none;
}

.title-text {
  margin-bottom: -5px;
  font-size: small;
  font-weight: 500;
}

.sub-text {
  font-family: "Garamond", serif;
  font-size: small;
}

.footer-playing .v-icon {
  padding-left: 15px;
}

.footer-wrap {
  display: grid;
  justify-items: center;
  align-items: center;
  justify-content: center;
  align-content: center;
}

.footer-icons .v-icon {
  margin-left: 13px;
}

.footer-progress {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.footer-progress p {
  margin-bottom: 0 !important;
  font-size: small;
}

.footer-sound {
  display: flex;
  flex-wrap: nowrap;
  align-content: center;
  justify-content: center;
  align-items: center;
}
</style>
