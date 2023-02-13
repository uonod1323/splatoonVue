<template>
    야임마!
    {{  }}
    <div>
        <p v-html="question"></p>
    </div>
</template>

<script>
export default {
    name: 'WeapontypePage',
    data(){
      return {
        weaponArray : [
            {
                name : '슬로셔',
                content : '당신에게는 정면 싸움보다 좋은 위치를 선점하고 일방적으로 목표를 타격하는 슬로셔가 어울립니다!',
                img : '',
            },
        ]
      }
    },

    methods : {
        setWeaponData : function(){
            
        }
    },

    props : {
        weaponType : String,
    },
}
</script>

<style>

</style>