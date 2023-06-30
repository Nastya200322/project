<template>
  <div>
    <button class="accordion" @click="toggleSection()">
      <div class="words">
        <span style="margin-left:12px;"><img src="../assets/vector.svg" ></span>
        <span style="margin-left:20px;">{{ name }}</span>
        <span style="margin-left:238px;"> {{ email }}</span>
        <span style="margin-left:274px;"> {{ phone }}</span>
        <span style="margin-left:285px;"> {{ website }}</span></div>
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
  data(){
    return{
      active:false,
      sections: [],
    }
  },
  props: {
    section: {
      type: Object,
      default(){
        return {}
      }
    },
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

<style>
.accordion {
  background-color: #fff;
  border: 1px solid var(--yellow, #FFD200);
  margin-bottom: 10px;
  width: 1626px;
  height: 40px;
  border-radius: 4px;
  margin-left:60px;
}

.active, .accordion:hover {
  background-color: #ccc; 
}

.words{
  display: flex;
  flex-shrink: 0;
  color: #696969;
  font-size: 14px;
  font-family: Roboto;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.panel {
  padding: 0 18px;
  background-color: white;
  overflow: hidden;
}

.active.panel {
  display: block;
}
</style>