<template>
  <div>
    <header class="site-header">{{ title }}</header>
    <hr />
    <div class="word"><p >
      <span style="margin-left:120px;" >Name</span>
      <span style="margin-left:307px;">Email</span>
      <span style="margin-left:350px;">Phone</span>
      <span style="margin-left:400px;">Website</span>
    </p></div>
    <accordion-section v-for="(section, index) in sections" :key="index" :section="section" >
      
    </accordion-section>
  </div>
</template>

<script>
import AccordionSection from "./components/AccordionSection.vue";


export default {
  components: {
    AccordionSection
  },
  data() {
    return {
      title: "USERS",
      sections: [],
    };
  },
  mounted() {
  fetch('https://jsonplaceholder.typicode.com/users')
    .then(response => response.json())
    .then(data => {
      console.log(data);
      this.sections = data;
    });
}
}
</script>

<style>
  header{
    color: var(--grey, #696969);
    font-size: 20px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    text-transform: uppercase;
    margin-top:24px;
    margin-left:51px;
  }

  hr{
    width: 100%;
    height: 0px;
    flex-shrink: 0;
    opacity: 0.3;
    margin-top:30px;
  }

  .word {
    color: #696969;
    font-size: 12px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    display: flex;
    width: 33.354px;
    flex-direction: column;
    flex-shrink: 0;
    margin-bottom:10px;
    opacity: 0.5;
  }
</style>