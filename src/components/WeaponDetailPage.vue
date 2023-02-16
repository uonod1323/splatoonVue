<template>
     <div class = "container">
    <div class="content-container">
      <div class="question-container">
        {{ this.weaponType }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'WeapontypePage',
    data(){
      return {
        weaponTypeName    : '',
        
      }
    },
    props : {
        weaponType : String,
    },
}
</script>

<style>

</style>