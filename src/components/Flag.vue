<template>
    <img :src="logo">
</template>
<script>
import unfinishedLogo from '../assets/unfinishedLogo.svg'
import completeLogo from '../assets/completeLogo.svg'
export default {
    name:'flag',
    data:function(){
        return {
            unfinishedLogo,
            completeLogo
        }
    },
    props:['status'],
    computed:{
        logo:function(){
            if(this.status)
                return this.completeLogo;
            else
                return this.unfinishedLogo;
        }
    }
}
</script>