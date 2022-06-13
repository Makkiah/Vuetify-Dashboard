<template>
    <div>
        <span
            class="tab"
            v-for="(tab, index) in tabs"
            :key="index"   
        >
            {{tab}}
        </span>
    </div>
</template>

<script>
export default {
    data(){
        return{
            tabs: ['Reviews', 'Make a Review']
        }
    }
}
</script>

<style>

</style>