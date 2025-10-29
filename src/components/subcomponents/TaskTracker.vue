<script>
    // TODO: Complete the code
    export default { 
        data() {
            return {
                
            }
        },
        // Hint: insert properties task (Object) and idx (Number)
        props :{
            task : Object,
            idx : Number
        },

        emits:[
            'removetask'
        ]
    }
</script>

<template>
    <!-- TODO: add your template code here --> 
     <div class="card" style="width: 18rem;">
            <div class="card-body">
                <h5 class="card-title">Deadline: {{ task.deadline }}</h5>
                <p class="card-text">{{ task.desc }}</p>
                <button class="btn btn-primart" @click="$emit('removeTask',idx)">Done</button>
            </div>
        </div>

   
</template>


