<template>
  <div class="CD-Container">
    <div class="city-group">
      <label for="city">Sehir</label>
      <select id="city" v-model="selectedCity" @change="getDistricts">
        <option v-for="city in citiesAndDistricts.data" :key="city.plaka_kodu">
          {{ city.il_adi }}
        </option>
      </select>
    </div>
    <div class="city-group">
      <label for="district">Ilce</label>
      <select v-model="selectedDistrict" @change="setValue">
        <option v-for="district in districts" :key="district.nufus">
          {{ district.ilce_adi }}
        </option>
      </select>
    </div>
  </div>
</template>

<script>
  import illerveilceler from "../../ililce.json";
  export default {
    name: "IlveIlce",
    data() {
      return {
        citiesAndDistricts: illerveilceler,
        selectedCity: null,
        districts: null,
        selectedDistrict: null,
      };
    },
    methods: {
      getDistricts() {
        this.citiesAndDistricts.data.forEach((il) => {
          if (this.selectedCity == il.il_adi) {
            this.districts = il.ilceler;
          }
        });
        this.setValue();
      },
      setValue() {
        this.$emit("input", {
          city: this.selectedCity,
          district: this.selectedDistrict,
        });
      },
    },
  };
</script>

<style scoped>
  .CD-Container {
    display: flex;
    flex-wrap: wrap;
  }
  .city-group {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  select {
    box-shadow: 0 3px 5px rgba(0, 0, 0, 0.2);
    padding: 0.5rem;
    background: white;
    margin: 0.2rem 0.2rem 1rem 0.2rem;
    width: 200px;
    font-size: 16px;
    color: #000000;
    border-radius: 0;
    display: inline-block;
  }
  select:focus-visible {
    outline: 0 !important;
  }

  label {
    font-weight: bold;
  }
  option {
    border-bottom: 1px solid #7a7979;
    border-left: 3px solid rgb(189, 189, 189);
    appearance: none;
  }

  option:hover {
    background-color: rgb(189, 189, 189);
    border-left: 3px solid #009670;
  }
</style>
