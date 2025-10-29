<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props:{
            subject: String,
            entry : String,
            mood: String
        },

        computed :{
            imgLoc (){
                // this assest is from public , use back quotes
                return `/assets/${this.mood.toLowerCase()}.png`
            }
        }

    }
</script>


<template>
    <!-- TODO: add your template code here. Use boostrap card --> 
     <slot>
        <div class="card" style="width: 18rem;">
            <!-- img is a dyncamic var so need to bind. :src -->
        <img :src="imgLoc" class="card-img-top" alt="...">
            <div class="card-body">
                <h5 class="card-title">{{ subject }}</h5>
                <p class="card-text">{{ entry }}</p>
            </div>
        </div>
        
     </slot>

</template>

