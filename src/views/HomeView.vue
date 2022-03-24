<template>
  <div class="home">
    <ul>
      <li v-for="item in commit" v-bind:key="item.sha">
        Commit<router-link :to ="'/about/' + item.sha">{{item.sha}}</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  
  data: function() {
    return {
    commit: [],
    }
  },

  async mounted(){
    let rez = await fetch("https://api.github.com/repos/vuejs/vue/commits")

    let pod = await rez.json()

    for(let item of pod){
      console.log(item.sha)
    }

    this.commit = pod;
  }, 
};
</script>
