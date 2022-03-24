<template>
  <div class="home">
    <ul>
      <li v-for="item in commit" :key="item.sha" @click="showabout(item.sha)">
        {{item.sha}}
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

  methods:{
    showabout(sha,ime,email,date){
      this.$router.push({ name: 'about', params: { sha: sha } })
      this.$router.push({ name: 'about', params: { ime: name } })
      this.$router.push({ name: 'about', params: { email: email } })
      this.$router.push({ name: 'about', params: { date: date } })
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
