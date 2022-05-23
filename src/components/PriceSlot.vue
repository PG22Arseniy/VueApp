<!--
<price-slot title="My Component"/> 

@copyright (c) 2022. Skudaev Arseniy. All Rights Reserved. 
-->
<template>

    <section class="price-slot-container" @click="doIt()">  <!-- Just one main element per template -->
        <div  v-if="slotState === 'price'" class="box price-slot" >{{ price }}</div>     
        <div v-if="slotState === 'answer'" class="box answer price-slot" id="answer">{{ answer }}</div>     
        <div v-if="slotState === 'question'" class="box question price-slot">{{ question }}</div>        
        <div>
            <!-- Put your HTML template here-->
            <slot></slot>
        </div> 
    </section>

</template>
<script>
    import Controller from '@/mixins/controller'

    // import other components you use here...

    class PriceSlotCtrl extends Controller {

        constructor( name, subComponentList = []) {
            super( name, subComponentList )

            // props passed in when using this component
            this.props = {
                price: String,
                answer: String,
                question: String,
                slotState: String  
            }              
           
        }
         onBeforeMount() {
            // default state is price
            this.slotState = "price" 
        }

                // Local component methods, used in a template they are called whenever it renders
        doIt( ) { 
            // onclick change between states
            switch  (this.slotState)
            {
                case "price" :
                    this.slotState = "answer" 
                    break;
                case "answer" :
                    this.slotState = "question"
                    break;
                case "question":
                    this.slotState = "price"
                    break;
                default : 
                    this.slotState = "price"
                    break;
                 
            }
      
        } 
    }
   // TODO: implement enums instead of strings
    const SlotState = { 
        PRICE: 0,
        ANSWER: 1,
        QUESTION: 2,
    };
    export default new PriceSlotCtrl('someTagName'/* , { subComponent, anotherComponent } */);

</script>
<style scoped>
    /*
    Add "scoped" attribute to limit CSS to this component only <style scoped>
    styles that are specific to this component only, not sub-children
    */


    .hide{
        display: none;
    }
    .box{
        text-align: center;
        margin: auto;
        padding: 20px;
        border: 3px solid blue; 
        color: darkblue;
        font-weight: bolder;
        font-size: 1.4rem; 
        width: fit-content; 
    } 
    
    .box:hover {
        background: darkblue;
        color: aliceblue; 
    }


</style>