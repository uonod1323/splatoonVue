<template>
   <div class = "container">
    <div class="content-container">
      <div class="question-container">
        <img :src = this.weaponImg />
        <p>{{ this.weaponName }}</p>
        <p class="result-content" v-html="weaponContent"></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'WeapontypePage',
    data(){
      return {
        weaponName    : '',
        weaponContent : '',
        weaponImg     : '',

        weaponArray : [
            {
                name : 'slosher',
                name_kor : '슬로셔',
                content : '당신에게는 정면 싸움보다 좋은 위치를 선점하고 \n 일방적으로 목표를 타격하는 슬로셔가 어울립니다!',
                img : require('../assets/weaponImg/slosher.jpg'),
            },
        ]
      }
    },

    mounted(){
      this.setWeaponData(this.weaponType);
    },

    methods : {
        setWeaponData : function(e){
            for(let i=0; i<this.weaponArray.length; i++){
                if(e === this.weaponArray[i].name){
                    this.weaponName = this.weaponArray[i].name_kor;
                    this.weaponContent = this.weaponArray[i].content.replace(/(?:\r\n|\r|\n)/g, '<br />');
                    this.weaponImg = this.weaponArray[i].img;
                }
            }
        }
    },

    props : {
        weaponType : String,
    },
}
</script>

<style>

</style>