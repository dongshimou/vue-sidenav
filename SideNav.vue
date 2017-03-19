<template >
<div id="nav">
    <slot></slot>
    </div>
</template>

<style>
#nav{
    background-color:#66ccff;
    display: block;
    transition: 0.3s;
    height: 100%;
    position: fixed;
    width: 0;
    top:0;
    left:0;
    overflow-x: hidden;
}
</style>

<script>
export default {
    name:'sidenav',
    methods: {
        isopen(){   
            this.$el.style.width=`${this.width}px`
            for(let one of this.$el.parentElement.children){
                one.style.marginLeft=`${this.width}px`;
            }
            this.$el.style.marginLeft="0";
        },
        isclose(){
            this.$el.style.width="0";
            for(let one of this.$el.parentElement.children){
                one.style.marginLeft="0";
            }
        }
    },
    watch: {
        open(value){
            open=value
            if(open)this.isopen()
            else this.isclose()
        }
    },
    props: {
        open:{
            type:Boolean,
            default:false
        },
        width:{
            type:Number,
            default:300
        }
    },
    computed: {
        
    }
}
</script>