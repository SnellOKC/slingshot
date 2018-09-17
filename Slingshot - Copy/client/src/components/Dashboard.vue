<template>
<v-app>
  <v-container fluid grid-list-lg >
    <v-layout row wrap style="height: 100%;">
      <v-flex xs12 sm6 md3>
        <div id="user" class="profile-bg dash-cards">
          <div style="padding-top: 40px">
          <img :src="user.pic" alt="avatar" class="user-avatar">
          <v-card-text class="user-name">{{user.name}}</v-card-text>
          <p id="jobtitle">{{user.title}}</p>
          </div>
          <v-tabs
      centered
      icons-and-text
      class="testy"
    >
      <v-tabs-slider color="blue lighten-4"></v-tabs-slider>
  
      <v-tab href="#news-feed">
        News Feed
        <img src="https://png.icons8.com/plasticine/30/000000/news.png" style="padding-bottom: 5px; margin-top: 5px;">
      </v-tab>
  
      <v-tab href="#trophy-case">
        Trophy Case
        <img src="https://png.icons8.com/plasticine/40/000000/uefa-euro-trophy.png">
      </v-tab>

      <v-tab-item
        id="news-feed"
      >
        <v-card flat>
          <v-card-text>{{ lorem }}</v-card-text>
        </v-card>
      </v-tab-item>

      <v-tab-item
        id="trophy-case"
      >
        <v-card flat>
          <v-card-text>{{ lorem }}</v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs>
        </div>
      </v-flex>
      
      <v-flex d-flex xs12 sm6 md5>
        <v-layout row wrap>
            <v-flex>
                <h5 id="headers">Goals</h5>
                <v-card id="goals" class="dash-cards">
                    <v-card-text>{{lorem}}</v-card-text>
                    <button ripple type="button" class="block">New Goal</button>
                </v-card>
            </v-flex>

            <v-flex>
                <h5 id="headers">Announcements</h5>
                <v-card id="news" class="dash-cards">
                    <v-card-text>{{lorem}}</v-card-text>
                </v-card>
            </v-flex>

        </v-layout>
      </v-flex>
      <v-flex xs12 sm6 md4>
          <h5 id="headers">Events</h5>
        <v-card id="events" class="dash-cards">
          <v-card-text>

<div>
    <v-expansion-panel>
      <v-expansion-panel-content>
        <div slot="header">Current Rank</div>
        <v-card>
          <v-card-text class="grey lighten-3">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</v-card-text>
        </v-card>
      </v-expansion-panel-content>
    </v-expansion-panel>
  </div>


          </v-card-text>
          
          <button type="button" class="block">New Event</button>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
  </v-app>
</template>

<script>
/*eslint-disable*/

 export default {
    name: 'dashboard',
    data: () => ({
        user: {
            name: 'Kyle Clarke',
            title: 'Senior Manager',
            pic: 'https://www.w3schools.com/howto/img_avatar.png'
        },
        contest: {
          name: 'Rookie Rumble'
        },
      lorem: `Lorem ipsum dolor sit amet, mel at clita quando. Te sit oratio vituperatoribus, nam ad ipsum posidonium mediocritatem, explicari dissentiunt cu mea. Repudiare disputationi vim in, mollis iriure nec cu, alienum argumentum ius ad. Pri eu justo aeque torquatos.`
    })
  }
</script>
<style type="text/css">

@media (min-width : 1024px)
{
  .v-tabs__container--fixed-tabs .v-tabs__div,
.v-tabs__container--icons-and-text .v-tabs__div,
.v-tabs
  {
    font-size: 12px;
    min-width: 10px;
  }
}
@media (min-width : 1920px)
{
  .v-tabs__container--fixed-tabs .v-tabs__div,
.v-tabs__container--icons-and-text .v-tabs__div,
.v-tabs
  {
    font-size: 14px;
    min-width: 10px;
  }
}

.v-tabs__container {
    width: 50%;
}

.v-expansion-panel__header {
  border-radius: 2px 2px 0 0;
  background: #5697fc;
  color: #ffffff;
  font-size: 16px;
  font-style: normal;
  font-stretch: normal;
  font-weight: 500;
  line-height: 27px;
  text-align: left;
  text-transform: none;
  letter-spacing: 0px;
  box-shadow: -11px 9px 21px 0px rgba(173,182,217,0.17);
  box-shadow: -2px 5px 6px 0px rgba(214,217,231,0.29);
}

.block {
    display: block;
    width: 100%;
    border: none;
    background-color: #83d497;
    color: #fff;
    padding: 10px;
    font-size: 16px;
    font-weight: 800;
    cursor: pointer;
    text-align: center;
    position: absolute;
    bottom: 0;
}

    .dash-cards {
        
        box-shadow: -11px 9px 21px 0px rgba(173,182,217,0.17);
        box-shadow: -2px 5px 6px 0px rgba(214,217,231,0.29);
    }

    .profile-bg {
        background: url("https://i.imgur.com/yDMGMHT.png") no-repeat center top;
        background-size: 100% auto;
    }

    .user-avatar {
        width: 40%;
        margin: auto; 
        display: block; 
        border-radius: 50%
    }

    .user-name {
  color: #4a4a4a;
  font-size: 1.2em;
  font-style: normal;
  font-stretch: normal;
  font-weight: 800;
  line-height: 24px;
  text-align: center;
  text-transform: none;
  letter-spacing: 0px;
  padding-bottom: 5px;
    }

    #user {
        height: calc(100% + 15px);
        background-color: #fff;
    }

    #goals, #news, #events {
        height: calc(100% - 40px);
        margin-top: 40px;
        overflow-y: auto;
        overflow-x: hidden;
        background: rgba(255, 255, 255, 0.6);
    }

    h5#headers {
        margin-bottom: -30px;
  color: #4a4a4a;
  font-size: 22px;
  font-style: normal;
  font-stretch: normal;
  font-weight: 400;
  line-height: 29px;
  text-transform: none;
  letter-spacing: 0px;
  
    }

    p#jobtitle {
          color: #757575;
          padding: 0;
  font-size: 1em;
  font-style: normal;
  font-stretch: normal;
  font-weight: 400;
  line-height: 19px;
  text-align: center;
  text-transform: none;
  letter-spacing: 0px;
    }
</style>

