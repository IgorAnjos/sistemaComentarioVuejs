<template>
    <div>
        <div class="form-todo form-group">
            <input v-model="name" type="text" name="author" placeholder="Nome" class="form-control">
            <br>
            <textarea v-model="message" class="form-control" name="message" placeholder="Comentário"></textarea>
        </div>
        <div>
            <button v-on:click="addComment" type="submit" class="btn btn-primary">Comentar</button>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                message: ''
            }
        },
        methods: {
            addComment() {
                if(this.message.trim() === ''){
                    alert('Preencha os campos');
                    return;
                }

                this.$emit('add-todo', {
                    name: this.name,
                    message: this.message
                });

                this.name = '';
                this.message= '';
            }
        }
    }
</script>