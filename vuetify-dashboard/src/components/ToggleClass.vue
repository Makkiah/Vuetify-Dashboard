<template>
    <div>
        <!-- Item Sale -->
        <div 
            class="center" 
            :class="[isActive ? 'active' : 'notActive', onSale ? 'sale' : 'noSale' ]" 
        >
            {{itemSale}} 
        </div>
        <!-- Toggle Active Class -->
        <v-btn 
            class="center" 
            @click="toggleActive(isActive)"
        >
            Toggle Active
        </v-btn>
        <!-- Toggle Sale Class -->
        <v-btn 
            class="center" 
            @click="toggleSale(onSale)"
        >
            Toggle Sale
        </v-btn>
        <!-- Hover Color Change -->
        <div
            @mouseover="changeColor"
            @mouseout="changeBack"
            class="center" 
            :style="{backgroundColor: propBGColor, color: propColor}"
        >
            Hover Me
        </div>
    </div>
</template>

<script>
export default {
    data(){
       return{
            isActive: true,
            onSale: false,
            brand: 'Prevail or Perish',
            product: 'T-Shirt',
            propBGColor: 'blue',
            propColor: 'white'
       }
    },
    computed: {
        itemSale(){
            if(this.onSale){
                return this.brand + ' ' + this.product + ' is on sale!'
            } else if(this.onSale === false){
                return this.brand + ' ' + this.product + ' is not on sale.'
            } else {
                return 'ERROR'
            }
        }
    },
    methods: {
        toggleActive(isActive){
            this.isActive = !isActive
        },
        toggleSale(onSale){
            this.onSale = !onSale
        },
        changeColor(){
            this.propBGColor = 'orange'
            this.propColor = 'black'
        },
        changeBack(){
            this.propBGColor = 'blue'
            this.propColor = 'white'
        }
    }
}
</script>

<style>
    .center{
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 5px auto;
    }
    .active{
        background-color: green;
        color: white;
    }
    .notActive{
        background-color: grey !important;
        color: black;
        user-select: none !important;
        cursor: not-allowed !important;
    }
    .sale{
        transform: scale(1.5);
        background-color: yellow;
        color: black;
    }
</style>