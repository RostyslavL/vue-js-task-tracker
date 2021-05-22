<template>
    <button
        @click="onClick()" 
        :style="{background: color}" 
        class="btn"> 
        <i class="fas fa-plus">
            &nbsp;{{ text }}
        </i>
    </button>
</template>


<script>

export default ({
    name:'Button',
    props: {
        text: String,
        color: String
    },
    methods:{
        onClick(){
            console.log('Button - onClick - invoced')
        }
    }
})
</script>
