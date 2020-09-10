<template>
  <div class="hello">
    <p style="color:red" v-if="kontrol==-1">Lütfen boş alan bırakmayın</p>
    <p style="color:green" v-else-if="kontrol==1">İl : {{secilenil}} ve İlçe : {{secilenilce}} olarak kaydedildi..</p>
    <label>
      <select name="il" v-model="secilenil" @change="check(secilenil)">
        <option v-for="il in json.data" :key="il.plaka_kodu">{{il.il_adi}}</option>
      </select>
    </label>
    <label>
      <select name="ilce" v-model="secilenilce">
        <option v-for="ilce in ilceler" :key="ilce.nufus">{{ilce.ilce_adi}}</option>
      </select>
    </label> <br> <br> <br>
    <button @click="kaydet">Kaydet</button>
  </div>
</template>

<script>
import illerveilceler from '../../ililce.json'
export default {
  name: 'IlveIlce',
  data(){
    return{
      json : illerveilceler,
      secilenil : '',
      ilceler : null,
      secilenilce:null,
      kontrol:0
    }
  },
  methods : {
    check(data){
      this.kontrol=0
      this.secilenilce=null
      console.log(this.secilenilce)
      let iller = this.json.data
      iller.forEach(il => {
        if(data==il.il_adi){
          this.ilceler=il.ilceler
        }
      });
    },
    kaydet(){
      if(this.secilenil=='' || this.secilenilce==null){
        this.kontrol=-1
      }else{
        this.kontrol=1
      }
    }
  }
}
</script>

<style scoped>
button{
  padding: 20px;
  border: 1px solid;
  border-radius: 30px;
  background: lightskyblue;
  width: 150px;
}

button:hover{
  background: lightgreen;
  cursor: pointer;
}
label{
  box-shadow:0 3px 5px rgba(0,0,0,.2);
  padding:15px;
  background:white;
  width:260px;
  display:inline-block;
  position:relative;
  margin-left:50px;
}

select{
  border:none;
  outline:none;
  display: inline-block;
  -webkit-appearance:none;
  -moz-appearance:none;
  appearance:none;
  cursor:pointer;
  font-size:16px;
  color:#909090;
  border-radius:0;
  width:275px;
  z-index:2;
  background:transparent;
}

label:after{
  content:"\25bc";
  font-size:16px;
  color:white;
  background:#009670;
  width:42px;
  text-align:center;
  line-height:3.2em;
  top:0;
  right:0;
  bottom:0;
  position:absolute;
  pointer-events:none;
}

option{
  border-bottom:1px solid #7a7979;
  border-left:3px solid rgb(189, 189, 189);
  appearance:none;
}

option:hover{
  background-color:rgb(189, 189, 189);
  border-left:3px solid #009670;
}
</style>
