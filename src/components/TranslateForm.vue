<template>
  <div id="translateForm">
    <form v-on:submit="formSubmit">
        <div class="form-group">
            <label>The Word</label>
            <input v-model="TextForTranslate" placeholder="Enter your word" class="form-control"> 
        </div>

        <div class="form-group">
            <select v-model="language" class="form-control">
                    <option value="ru">Russian</option>
                    <option value="es">Spanish</option>
                    <option value="fr">French</option>
                    <option value="it">Italian</option>
            </select>
        </div>
        
        <input type="submit" value="Translate" class="btn btn-success">
    </form>
  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data(){
        return{
            TextForTranslate:'',
            language:''
        }
    },
    created(){
        this.language = 'ru';
    },
    methods:{
        formSubmit(e){
            this.$emit('formSubmit',this.TextForTranslate , this.language);
            e.preventDefault();
        }
    }
  }
</script>

<style>

</style>
