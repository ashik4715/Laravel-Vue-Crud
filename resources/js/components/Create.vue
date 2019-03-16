<template>
    <div>
        <h2>Add New User</h2>
        <hr>
        <form class="form-group" method="POST" action="/users">

            <div class="form-group">
                <label class="col-sm-2" for="name"><h5><b>Name:</b></h5></label>
                <div class="col-sm-10">
                    <input type="text" class="form-control" id="name" name="name" placeholder="Enter Name" v-model="name">
                </div>
            </div>

            <div class="form-group">
                <label class="col-sm-2" for="email"><h5><b>Email:</b></h5></label>
                <div class="col-sm-10">
                    <input type="email" class="form-control" id="email" name="email" placeholder="Enter Email" v-model="email">
                </div>
            </div>

            <div class="form-group">
                <label class="col-sm-2" for="password"><h5><b>Password:</b></h5></label>
                <div class="col-sm-10">
                    <input type="password" class="form-control" id="password" name="password" placeholder="Enter Password" v-model="password">
                </div>
            </div>

            <div class="form-group">
                <div class="col-sm-2">
                    <button type="button" style="cursor:pointer" class="btn btn-block btn-outline-info" v-on:click="addNewUser()" >
                        Save
                    </button>
                </div>
            </div>

        </form>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                name: '',
                email: '',
                password: '',
            }
        },
        methods: {
            addNewUser(){

                axios.post('/api/users',{
                    name: this.name,
                    email: this.email,
                    password: this.password
                }).then(response => {
                    console.log(response)
                    this.name = ''
                    this.email = ''
                    this.password = ''
                }).catch(error => {
                    console.log(error)
                })

            }
        }
    }
</script>

<style scoped>

</style>