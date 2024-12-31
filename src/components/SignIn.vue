<template>

    <div class="container px-lg-5 ">
        <h2> Registration Page</h2>
        <div> {{ form.fullname }} {{ form.email }} {{ form.mobNumber }}
            {{ form.city }} {{ form.gender }} {{ form.hobby }} {{ form.messege }}
        </div>
        <form @submit="handleForm">
            <div class="row text-start p-lg-5 mx-lg-5 alert-dark">
                <h3 class=""> Form </h3>
                <div class="col-lg-6 py-1">
                    <label> fullName </label>
                    <input type="text" v-model="form.fullname" class=" form-control" name="ful_name"
                        @keypress="isLetter($event)" />
                    <p v-if="alphaMsg" style="color:#ba0000; text-align: left;"> {{ alphaMsg }} </p>
                </div>
                <div class="col-lg-6 py-1">
                    <label> email </label>
                    <input type="email" v-model="form.email" class=" form-control " name="email" />
                </div>

                <div class="col-lg-6 py-1">
                    <label> Mobile Number </label>
                    <input type="number" v-model="form.mobNumber" class=" form-control " name="mob_number" />
                </div>

                <div class="col-lg-6 py-1">
                    <label> City </label>
                    <select class="form-select" v-model="form.city" aria-label="Default select example">
                        <option selected>Open this select menu</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>

                <div class="col-lg-6 py-1">
                    <label class="w-100 pt-2"> What is Your Gender </label>
                    <label class="pe-3">
                        <input type="radio" v-model="form.gender" id="male" value="male" name="gender"> Male
                    </label>
                    <label class="pe-3">
                        <input type="radio" v-model="form.gender" id="female" value="female" name="gender"> Female
                    </label>
                </div>

                <div class="col-lg-6 py-1">
                    <label class="w-100 pt-2"> Select Your Hobbies </label>
                    <label v-for="(data, index) in hobbydata" :key="index" class="pe-3">
                        <input type="checkbox" v-model="form.hobby" :value="data"> {{ data }}
                    </label>

                </div>

                <div class="col-lg-12 py-1">
                    <textarea v-model="form.messege" class="form-control" id="exampleFormControlTextarea1"
                        rows="3"></textarea>
                </div>
                <div class="col-lg-4 py-2">
                    <button type="submit" class="btn  btn-dark "> Submit </button>
                </div>
                <div class="col-lg-4 py-2">
                    <button type="button" class="btn  btn-dark " @click="fetchData()"> Get Data </button>
                </div>
                <table class="table table-striped" v-if="tableshow">
                    <thead>
                        <tr >
                            <th scope="col">Id</th>
                            <th scope="col">Name</th>
                            <th scope="col">Email</th>
                            <th scope="col">city</th>
                            <th scope="col">Zipcode</th>
                            
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(data, index) in response" :key="index" >
                            <th scope="row"> {{ data.id }} </th>
                            <td> {{ data.name }} </td>
                            <td> {{ data.email }} </td>
                            <td> {{ data.address.city }} </td>
                            <td> {{ data.address.zipcode }} </td>
                            
                        </tr>

                    </tbody>
                </table>


            </div>
        </form>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "SignIn",

    data() {
        return {
            form: {
                fullname: '',
                email: '',
                mobNumber: '',
                city: '',
                messege: '',
                gender: '',
                hobby: []

            },
            alphaMsg: '',
            hobbydata: ['singing', 'dancing', 'reading'],
            tableshow: false, // by default table heading will hidden
            response: []

        }
    },

    methods: {
        handleForm(e) {
            e.preventDefault();
            let formdata = JSON.stringify(this.form)
            let finaldata = JSON.parse(formdata)
            console.log(finaldata)
        },
        isLetter(e) {
            let char = String.fromCharCode(e.keyCode);
            if (/^[A-Za-z]+$/.test(char)) return true;
            else e.preventDefault();
            this.alphaMsg = "Only letters Allowed";
        },
        fetchData() {
           
            axios({
                method: 'get',
                url: 'https://jsonplaceholder.typicode.com/users'
            })
                .then((response) => {
                    this.tableshow = true;  // this is for show table heading
                    this.response = response.data; // this is for show api data
                    console.log(response.data)
                })
                .catch((err) => {
                    console.log(err)
                })

        }

    }

}


</script>