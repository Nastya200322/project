<template>
  <div>
    <button class="accordion" @click="toggleSection()">
      <div class="words">
        <span><img src="../assets/vector.svg" ></span>
        <span class="info">{{ name }}</span>
        <span class="info"> {{ email }}</span>
        <span class="info"> {{ phone }}</span>
        <span class="info"> {{ website }}</span></div>
    </button>
    <div class="panel">
      <submit-section v-if="active" :section="section"/>
    </div>
  </div>
</template>

<script>
import SubmitSection from "@/components/SubmitSection.vue";

export default {
  components: {
    SubmitSection
  },
  props: {
    section: {
      type: Object,
      default(){
        return {}
      }
    },
  },
  data(){
    return{
      active:false,
      sections: [],
    }
  },
  
  computed:{
    name(){
      return this.section?.name
    },
    email(){
      return this.section?.email
    },
    phone(){
      return this.section?.phone
    },
    website(){
      return this.section?.website
    }
  },
  methods: {
    toggleSection() {
      this.active = !this.active;
    }
  }
};
</script>

<style scoped>
.accordion {
  background-color: #fff;
  border: 1px solid  #FFD200;
  border-radius: 4px;
  margin-bottom:10px;
  width: 100%;
  height: 40px;
}

.active, .accordion:hover {
  background-color: #ccc; 
}

.words {
  display: flex;
  justify-content: space-between;
  color: #696969;
  font-size: 14px;
  font-family: Roboto;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.info {
  width: 400px;
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.panel {
  background-color: white;
  overflow: hidden;
}

.active.panel {
  display: block;
}
</style>