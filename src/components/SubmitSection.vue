<template>
  <div class="tab-btn">
    <table>
      <tr>
        <th>ADDRESS</th>
        <th>COMPANY</th>
        <th>BASIC INFO</th>
      </tr>
      <tr>
        <td v-for="(fieldGroup, index) in fields" :key="index">
          <p v-for="(field, fieldIndex) in fieldGroup.fields" :key="fieldIndex">
            <b>{{ field.label }}</b><br>
            <input type="text" size="50" :ref="field.ref" :value="field.value" />
          </p>
        </td>
      </tr>
    </table>
    <button class="btn-submit" @click="alertSection()">
      <img src="../assets/vectortwo.svg" >
    </button>
  </div>
</template>

<script>
export default {
  props: {
    section: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  computed: {
    address() {
      return this.section.address;
    },
    company() {
      return this.section.company;
    },
    fields() {
      return [
        {
          section: 'address',
          fields: [
            { label: "Street", ref: "streetInput", value: this.address?.street },
            { label: "Suite", ref: "suiteInput", value: this.address?.suite },
            { label: "City", ref: "cityInput", value: this.address?.city },
            { label: "Zipcode", ref: "zipcodeInput", value: this.address?.zipcode }
          ]
        },
        {
          section: 'company',
          fields: [
            { label: "Name", ref: "namecomInput", value: this.company?.name },
            { label: "CatchPhrase", ref: "catchPhraseInput", value: this.company?.catchPhrase },
            { label: "Bs", ref: "bsInput", value: this.company?.bs }
          ]
        },
        {
          fields: [
            { label: "Name", ref: "nameInput", value: this.section?.name },
            { label: "Username", ref: "usernameInput", value: this.section?.username },
            { label: "Email", ref: "emailInput", value: this.section?.email },
            { label: "Phone", ref: "phoneInput", value: this.section?.phone },
            { label: "Website", ref: "websiteInput", value: this.section?.website }
          ]
        }
      ];
    }
  },
  data() {
    return {
      edited: false,
    };
  },
  methods: {
    alertSection() {
      let editedFields = [];
      this.fields.forEach((fieldGroup) => {
        fieldGroup.fields.forEach((field) => {
          const newValue = this.$refs[field.ref][0].value;
          if (field.value !== newValue) {
            editedFields.push(`${field.label}: ${newValue}`);
          }
        });
      });
      if (editedFields.length > 0) {
        this.edited = true;
        alert("Отредактировано:\n" + editedFields.join("\n"));
      }
    }
  }
}
</script>
  
<style scoped>

  table {
    border-collapse: collapse;
    border: 1px solid lightgrey;
    border-radius: 4px;
    width: 1501px;
    height: 406px;
  }
  
  th,td {
    border: 1px solid lightgrey;
    padding: 10px;
    color:  #696969;
    font-size: 16px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    margin-left: 30px;
    height: 18px; 
    vertical-align: top;
    text-align: left;
  }
  
  b{
    opacity: 0.5;
    color: #696969;
    font-size: 12px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
  }
  
  .btn-submit {
    width: 41px;
    height: 40px;
    border: none;
    background-color: #FFD300;
    border-radius: 4px;
    margin-left: 20px;
  }

  .tab-btn{
    display: flex;
    margin-bottom: 20px;
    margin-top: 12px;
    margin-left: 91px;
  }

  input{
    height: 35px; 
    width: 433px;
    color: #696969;
    font-size: 14px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    border: 1px solid  #D9DBDA;
    border-radius: 4px;
  }
  </style>