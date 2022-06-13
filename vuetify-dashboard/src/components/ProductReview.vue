<template>
    <div>
        <!-- Names added to namesArray via form submission -->
        <div
            class="center border" 
            @name-submitted="addName"
        >
            <ul>
                <li 
                    v-for="(obj, index) in namesArray"
                    :key="index"
                >
                    {{obj.name}} answered '{{obj.recommend}}' to whether they would recommend this product.
                </li>
            </ul>   
        </div>
        <!-- Form -->
        <form @submit.prevent="onSubmit">
            <!-- Form Custom Validation -->
            <ul v-if="errors.length">
                <p>Please, tend to the following errors: </p>
                <li v-for="(error, index) in errors" :key="index">{{error}}</li>
            </ul>
            <!-- Form input -->
            <input class="center border" type="text" v-model="fName" placeholder="First Name" >
            <input class="center border" type="text" v-model="lName" placeholder="Last Name" >
            <!-- Form Radio Btn Question -->
            <div class="center border">
                <p>Whould you recommend this form?</p>
                <input type="radio" id="yesRadio" value= "Yes" name="recommend" v-model="recommendation">
                <label for="yesRadio" >Yes</label>
                <input type="radio" id="noRadio" value= "No" name="recommend" v-model="recommendation">
                <label for="noRadio" >No</label>
            </div>
            <!-- Form Submit -->
            <input class="center border" type="submit" value="Submit">
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return {
            fName: null,
            lName: null,
            recommendation: null,
            namesArray: [],
            errors: []
        }
    },
    methods: {
        onSubmit(){
            if(this.fName && this.lName && this.recommendation){
                let nArray = {
                    name: this.fName + ' '  + this.lName,
                    recommend: this.recommendation
                }
                this.$emit('name-submitted', nArray)
                this.namesArray.push(nArray)
                this.fName = ''
                this.lName = ''
                this.recommendation = null
                this.errors = []
            } else {
                this.errors = []
                if(!this.fName){this.errors.push("First Name Required")}
                if(!this.lName){this.errors.push("Last Name Required")}
                if(!this.recommendation){this.errors.push("Recommendation Option Required")}
            }
        },
        addName(nArray){
            this.namesArray.push(nArray.name)
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
    .border{
        border: 1px solid black;
    }
</style>