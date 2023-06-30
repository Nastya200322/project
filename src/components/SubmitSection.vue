<template>
    <div class="tab-btn">
      <table>
        <tr>
          <th >ADDRESS</th>
          <th>COMPANY</th>
          <th>BASIC INFO</th>
        </tr>
        <tr>
          <td>
            <p><b>Street </b><br />
              <input type="text" size="50"  :value="section.address?.street" ref="streetInput"/>
            </p>
            <p><b>Suite</b><br />
              <input type="text" size="50" :value="section.address?.suite" ref="suiteInput"/>
            </p>
            <p><b>City</b><br />
              <input type="text" size="50" :value="section.address?.city" ref="cityInput"/>
            </p>
            <p><b>Zipcode</b><br />
              <input type="text" size="50" :value="section.address?.zipcode" ref="zipcodeInput" />
            </p>
          </td>
          <td >
            <p><b>Name</b><br/>
              <input type="text" size="50" :value="section.company?.name" ref="namecomInput"/>
            </p>
            <p><b>CatchPhrase</b><br />
              <input type="text" size="50" :value="section.company?.catchPhrase" ref="catchPhraseInput"/>
            </p>
            <p><b>Bs</b><br />
              <input type="text" size="50" :value="section.company?.bs" ref="bsInput"/>
            </p>
          </td>
          <td>
            <p><b>Name</b><br />
              <input type="text" size="50"  :value="section?.name" ref="nameInput"/>
            </p>
            <p><b>Username</b><br />
              <input type="text" size="50" :value="section?.username" ref="usernameInput"/>
            </p>
            <p><b>Email</b><br />
              <input type="text" size="50" :value="section?.email" ref="emailInput"/>
            </p>
            <p><b>Phone</b><br />
              <input type="text" size="50" :value="section?.phone" ref="phoneInput"/>
            </p>
            <p><b>Website</b><br />
              <input type="text" size="50" :value="section?.website" ref="websiteInput"/>
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
        return {}
      }
    },
  },
  data() {
    return {
      edited: false
    }
  },
  methods: {
    alertSection() {
      if (this.section.address?.street !== this.$refs.streetInput.value ||
        this.section.address?.suite !== this.$refs.suiteInput.value ||
        this.section.address?.city !== this.$refs.cityInput.value ||
        this.section.address?.zipcode !== this.$refs.zipcodeInput.value ||
        this.section.company?.name !== this.$refs.namecomInput.value ||
        this.section.company?.catchPhrase !== this.$refs.catchPhraseInput.value ||
        this.section.company?.bs !== this.$refs.bsInput.value ||
        this.section?.name !== this.$refs.nameInput.value ||
        this.section?.username !== this.$refs.usernameInput.value ||
        this.section?.email !== this.$refs.emailInput.value ||
        this.section?.phone !== this.$refs.phoneInput.value ||
        this.section?.website !== this.$refs.websiteInput.value) {
          this.edited = true;
          if (this.edited) {
            alert("Отредактировано: " +
            (this.section.address?.street !== this.$refs.streetInput.value ? "Street " : "") +
            (this.section.address?.suite !== this.$refs.suiteInput.value ? "Suite " : "") +
            (this.section.address?.city !== this.$refs.cityInput.value ? "City " : "") +
            (this.section.address?.zipcode !== this.$refs.zipcodeInput.value ? "Zipcode " : "") +
            (this.section.company?.name !== this.$refs.namecomInput.value ? "Company Name " : "") +
            (this.section.company?.catchPhrase !== this.$refs.catchPhraseInput.value ? "CatchPhrase " : "") +
            (this.section.company?.bs !== this.$refs.bsInput.value ? "Bs " : "") +
            (this.section?.name !== this.$refs.nameInput.value ? "Name " : "") +
            (this.section?.username !== this.$refs.usernameInput.value ? "Username " : "") +
            (this.section?.email !== this.$refs.emailInput.value ? "Email " : "") +
            (this.section?.phone !== this.$refs.phoneInput.value ? "Phone " : "") +
            (this.section?.website !== this.$refs.websiteInput.value ? "Website" : "")
            );
          }
        }
    }
  }
}
</script>
  
  <style>
  table {
    border-collapse: collapse;
    border: 1px solid lightgrey;
    width: 1501px;
    height: 406px;
    border-radius: 4px;
  }
  
  th,td {
    border: 1px solid lightgrey;
    padding: 10px;
    color: var(--grey, #696969);
    font-size: 16px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    margin-left:30px;
    height: 18px; vertical-align: top;
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
    margin-left:20px;
  }

  .tab-btn{
    display: flex;
    margin-bottom: 20px;
    margin-top: 12px;
    margin-left: 91px;
  }

  input{
    height: 35px; width: 433px;
    color: #696969;
    font-size: 14px;
    font-family: Roboto;
    font-style: normal;
    font-weight: 400;
    line-height: normal;border-radius: 4px;
    border: 1px solid var(--light-grey, #D9DBDA);
  }
  </style>