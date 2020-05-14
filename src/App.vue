<template>
  <div id="app">
    <my-header @clickMenuA="clickMenuA"
               @clickMenuB="clickMenuB"
               @clickMenuC="clickMenuC"
    ></my-header>
    <my-person-info v-if="state==='HOMEPAGE'"
                    @clickInfoChange="clickInfoChange"
    ></my-person-info>
    <mainpage-bar v-if="state==='HOMEPAGE'"></mainpage-bar>
    <notification-list v-if="state==='HOMEPAGE' && homeState==='NOTIF'"></notification-list>
    <change-info v-if="state==='HOMECHANGEINFO'"
                 @clickReturn="clickInfoChangeReturn"
                 @clickConfirm="clickInfoChangeConfirm"
    ></change-info>
    <msg-sidebar v-if="state==='TOPIC'"
                 @clickShowCategory="clickShowCategory"
                 @clickCreate="clickCreateC"
                 topicMode="clear"
    ></msg-sidebar>
    <div v-if="state==='CREATETOPICCAT'" id="createtopichint">
      <h1>请选择您的分类</h1>
    </div>
    <msg-sidebar v-if="state==='ATOPIC'"
                 @clickShowCategory="clickShowCategory"
                 @clickCreate="clickCreateA"
                 topicMode="anonymous"
    ></msg-sidebar>
    <category v-if="this.state==='TOPICSHOWCATEGORY' || this.state==='CREATETOPICCAT'"></category>
    <div v-if="state==='CREATETOPICCAT'" id="createtopicbtn">
      <a-button type="primary" @click="gotoCreateTopic">下一步</a-button>
    </div>
    <topic-detail v-if="state==='TOPICDETAIL'"></topic-detail>
    <create-topic v-if="state==='CREATETOPIC'"
                  @submitTopic="submitTopic"
                  @throwTopic="throwTopic"
    ></create-topic>
  </div>
</template>

<script>
  import MyHeader from './components/header.vue'
  import MyPersonInfo from './components/personInfo.vue'
  import MainpageBar from './components/mainpageBar.vue'
  import NotificationList from './components/notificationList.vue'
  import ChangeInfo from './components/changeInfo.vue'
  import MsgSidebar from './components/msgSidebar.vue'
  import Category from './components/category.vue'
  import TopicDetail from './components/topicDetail.vue'
  import CreateTopic from './components/createTopic.vue'
export default {
  name: 'App',
  components: {
    MyHeader,
    MyPersonInfo,
    MainpageBar,
    NotificationList,
    ChangeInfo,
    MsgSidebar,
    Category,
    TopicDetail,
    CreateTopic
  },
  data: function () {
    return {
      state: 'HOMEPAGE',
      homeState: 'NOTIF',
      categoryState: 'false'  // possibly useless
    }
  },
  methods: {
    clickMenuA: function () {
      console.log('Get clickMenuA')
      this.state = 'HOMEPAGE'
      this.homeState = 'NOTIF'  // Default homepage set to notification
    },
    clickMenuB: function () {
      console.log('Get clickMenuB')
      this.state = 'TOPIC'
    },
    clickMenuC: function () {
      console.log('Get clickMenuC')
      this.state = 'ATOPIC'
    },
    clickInfoChange: function () {
      console.log('Get clickInfoChange')
      this.state = 'HOMECHANGEINFO'
    },
    clickInfoChangeConfirm: function () {
      console.log('Get clickInfoChangeConfirm')
      this.state = 'HOMEPAGE'
    },
    clickInfoChangeReturn: function () {
      console.log('Get clickInfoChangeReturn')
      this.state = 'HOMEPAGE'
    },
    clickShowCategory: function () {
      console.log('Get clickShowCategory')
      this.categoryState = 'true'   //possibly useless
      this.state = 'TOPICSHOWCATEGORY'
    },
    clickCreateC: function () {
      console.log('Get clickCreateC')
      this.state = 'CREATETOPICCAT'
    },
    clickCreateA: function () {
      console.log('Get clickCreateA')
      this.state = 'CREATETOPICCAT'
    },
    gotoCreateTopic: function () {
      this.state = 'CREATETOPIC'
    },
    submitTopic: function () {
      console.log('Get submitTopic')
      this.state = 'TOPICDETAIL'
    },
    throwTopic: function () {
      console.log('Get throwTopic')
      this.state = 'TOPIC'
    }
  }
}
</script>

<style>
#createtopichint {
  width: 67%;
  margin: 15px auto;
  text-align: center;
}
#createtopicbtn {
  width: 67%;
  margin: 15px auto;
  text-align: center;
}
</style>
