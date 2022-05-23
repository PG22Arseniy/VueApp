<!--
VFS VUE Single File Component
Copyright (c) 2022. Arseniy Skudaev, Kibble Online Inc. All Rights Reserved.
-->
<template>

    <section class="slot-container">
        <div class="slot">
            <price-slot price = "1000" answer="Copyright (c) 2018. Scott Henshaw, Kibble Online Inc. All Rights Reserved." question = "3000" number = "0"/>        
        </div>
    </section>

</template>
<script>
    import Controller from '@/mixins/controller'

    import PriceSlot from '@/components/PriceSlot.vue' 

    class TestCtrl extends Controller {

        constructor( name, subComponentList = []) {
            super( name, subComponentList );
            this.vm = {
                name: 'Vue Jeopardy',
            }
        }
    }

    export default new TestCtrl('pgAbout', { PriceSlot });  

</script>
<style>
/* Local styles for this template */
    .slot-container{
        grid-column-start: 6;   
        display: flex; 
        justify-content: center;
        align-content: center;
        align-items: center; 
    }
    .slot{
        margin: auto; 
    }
    .test-container {
        display: inline-block;
        width: 100%;
    }

    .test {
        margin:2vw;
        border: 1px solid black;
        background-color: lightgray;
        color: black;
        height: 78vh;
        width: 80vw;
    }

    .title {
        text-shadow: 2px 2px #777;
    }
</style>
