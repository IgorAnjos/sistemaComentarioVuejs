<template>
        <div class="container">
            <h1>Comentários</h1>
            <hr>
            <FormComment v-on:add-todo="addComment"></FormComment>            
            <br>
            <div class="list-group">
                <p v-if="comments.length <= 0">Sem domentários...</p>
                <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index"> <!-- Necessário colocar v-bind:key -->
                    <span class="comment__Author">Autor: <strong>{{ comment.name }}</strong></span>
                    <p>
                        {{ comment.message }}
                    </p>
                    <div>
                        <a v-on:click="removeComment(index)" href="#" title="Excluir">Excluir</a>
                    </div>
                </div>
            </div>
        </div>
</template>

<script>
import FormComment from './FormComment';

export default {
    components: {
        FormComment
    },
    data() { // mesma coisa de "data function()"
        return {
            comments: []
        }
    },
    methods: {
        addComment(comment){
            this.comments.push(comment);
        },
        removeComment(index){
            console.log(index);
            this.comments.splice(index, 1);
        }
    },
    computed: {
        allComments(){
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
        }
    },
    watch: {
        comments(val){
            console.log('val', val)
        }
    }
}
</script>