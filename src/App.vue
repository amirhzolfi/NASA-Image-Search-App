<template>
  <div>
    <WelcomeScreen v-if="showWelcomScreen"/>
    <ListWrapper v-else />
  </div>

 
</template>

<script>
import ListWrapper from './components/listWrapper.vue';
import WelcomeScreen from './components/welcomeScreen.vue';


export default {
  name: 'App',
  components: {
    WelcomeScreen,
    ListWrapper,
  
  },
  data() {
    return {
      showWelcomScreen: true
    }
  },
  created () {
    setTimeout(() => {
      document.body.style.padding = '20px'
      document.body.style.overflow = 'auto'
      this.showWelcomScreen = false;
      
    }, 5000);
  }
}
</script>

<style>

::-webkit-scrollbar {
  width: 5px;
}

/* Track */
::-webkit-scrollbar-track {
  background: navy;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: red;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: darkred;
}
body {
  padding: 0px;
  margin: 0px;
  box-sizing:border-box;
  background-color: #0b3d91;
  color: white;
  overflow: hidden;
}
</style>
