<template>
    <div>
        <div class="alert alert-success" v-if="showSuccess">             
            <button type="button" class="close-btn" v-on:click="showSuccess=false">&times;</button>
            <strong>{{ successMessage }}</strong>
        </div>
        <user-edit :user="profileUser" @user-saved="savedUser" @user-canceled="cancelEdit"></user-edit>
    </div>              
</template>

<script type="text/javascript">    
    import userEdit from './userEdit.vue';

    export default {
        components: {
            'user-edit': userEdit, 
        },
        data: function(){
            return { 
                profileUser: {
                    email:"",
                    name:""
                },
                successMessage: "",
                showSuccess: false
            }
        },
        methods: {
            savedUser: function(){
                this.showSuccess = true;
                this.successMessage = "User's Profile Updated";
            },
            cancelEdit: function(){
                this.showSuccess = false;
            },            
        },
        mounted() {
            this.getInformationFromLoggedUser();
        }        
    }
</script>