<template>
    <div>
        <h2>Edit User</h2>
        <hr>
        <form class="form-group" method="POST" action="/users">

            <div class="form-group">
                <label class="col-sm-2" for="name"><h5><b>Name:</b></h5></label>
                <div class="col-sm-10">
                    <input type="text" class="form-control" id="name" name="name" placeholder="Enter Name"
                           v-model="name">
                </div>
            </div>

            <div class="form-group">
                <label class="col-sm-2" for="email"><h5><b>Email:</b></h5></label>
                <div class="col-sm-10">
                    <input type="email" class="form-control" id="email" name="email" placeholder="Enter Email"
                           v-model="email">
                </div>
            </div>

            <div class="form-group">
                <label class="col-sm-2" for="password"><h5><b>Password:</b></h5></label>
                <div class="col-sm-10">
                    <input type="password" class="form-control" id="password" name="password"
                           placeholder="Enter Password" v-model="password">
                </div>
            </div>

            <div class="form-group">
                <div class="col-sm-2">
                    <button type="button" style="cursor:pointer" class="btn btn-block btn-outline-info"
                            v-on:click="UpdateUser()">
                        Update
                    </button>
                </div>
            </div>

        </form>
    </div>
</template>

<script>
    export default {
        props: ['id'],
        data() {
            return {
                name: '',
                email: '',
                password: '',
            }
        },
        mounted() {
            axios.get('/api/users/' + this.id).then(response => {
                let user = response.data;
                this.name = user.name;
                this.email = user.email;
                this.password = user.password;
            }).catch(error => {
                console.log(error)
            })
        },
        methods: {
            UpdateUser() {
                axios.put('/api/users/' + this.id, {
                    name: this.name,
                    email: this.email,
                    password: this.password
            }).then(response => {
                    console.log(response)
                }).catch(error => {
                    console.log(error)
                })
            }
        }
    }
</script>

<style scoped>

</style>