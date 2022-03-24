<template>
  <div class="About">
    {{sha}}
    
  </div>
</template>

<script>
export default{
  name: 'About',

  data: function(){
    return{
      sha: "",
      ime: "",
      email: "",
      date: ""
    }
  },

  async mounted(){
    this.sha = this.$route.params.sha

    let rez = await fetch("https://api.github.com/repos/vuejs/vue/commits/" + this.$route.params.sha)
    let pod = await rez.json()

    console.log(pod)
  }

};
</script>
