<template>
    <div>
        <p></p>
        <div>
            <form id="lista-form" @submit="createUser">
                <div class ="input-container">
                    <label for="id">Id: </label>
                    <input type="text" id="id" name="id" v-model="id" placeholder="Digite o id">
                </div>
                <div class ="input-container">
                    <label for="firstName">Nome: </label>
                    <input type="text" id="firstName" name="firstName" v-model="firstName" placeholder="Digite o nome">
                </div>
                <div class ="input-container">
                    <label for="endereço">Sobrenome:</label>
                    <input type="text" id="lastName" name="lastName" v-model="lastName" placeholder="Digite o sobrenome">
                </div>
                <div class ="input-container">
                    <label for="id">Email:</label>
                    <input type="text" id="email" name="email" v-model="email" placeholder="Digite o email">
                </div>
                <div class ="input-container">
                    <label for="id">Endereço:</label>
                    <input type="text" id="adress" name="adress" v-model="adress" placeholder="Digite o endereço">
                </div>
                <input type="submit" class="submit-btn" value="Cadastrar">
            </form>
        </div>
    </div>
</template>

<script>
export default {
    name: "ListaForm",
    data(){
        return {
            users: [],
            id: null,
            firstName: null,
            lastName: null,
            email: null,
            adress: null
            
        }
    },
    methods: {
        async getUsers(){
            const req = await fetch("http://localhost:3000/users");
            const data = await req.json();

            this.users = data.users;         
    },

    async createrUser(e){

        e.preventDefault();

        const data = {
            id: this.id,
            firstName: this.firstName,
            lastName: this.lastName,
            email: this.email,
            adress: this.adress
        }

        const dataJson = JSON.stringify(data);

        const req = await fetch("http://localhost:3000/users", {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: dataJson
        });

        const res = await req.json();

        console.log(res);
        
    },
    mounted() {
        this.getUsers()
    },
    
    }
}
</script>

<style scoped>
    #lista-form{
        max-width: 400px;
        margin: 0 auto;
    }
    .input-container{
        display: flex;
        flex-direction: column;
        margin-bottom: 10px;
    }

    label{
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;
    }

    input, select {
        padding : 5px 10px;
        width: 300px;
    }

    #opcionais-container {
        flex-direction: row;
        flex-wrap: wrap;
    }

    .submit-btn {
        background-color: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

    .submit-btn:hover{
        background-color: transparent;
        color: #222;
    }

</style>
