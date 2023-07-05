<template>
  <div>
    <header class="site-header">{{ title }}</header>
    <hr />
    <div class="word">
        <span v-for="(field, index) in fields" :key="index"  class="field">{{ field }}</span>
    </div>
    <accordion-section v-for="(section, index) in sections" :key="index" :section="section" />
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
      fields: ["Name", "Email", "Phone", "Website"]
    };
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      fetch('https://jsonplaceholder.typicode.com/users')
        .then(response => response.json())
        .then(data => {
          console.log(data);
          this.sections = data;
        });
    }
  }
}
</script>

<style scoped>
  header{
    color:  #696969;
    font-size: 20px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 500;
    line-height: normal;
    text-transform: uppercase;
    margin: 24px 0 0 51px;
  }

  hr{
    width: 100%;
    flex-shrink: 0;
    opacity: 0.3;
    margin-top: 30px;
  }

  .word {
    color: #696969;
    font-size: 12px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    display: flex;
    justify-content: space-around;
    opacity: 0.5;
  }

  .field {
    padding: 10px 0;
    width: 280px;
    text-align: left;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
</style>