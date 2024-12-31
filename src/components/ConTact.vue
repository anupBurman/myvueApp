<template>
    <h2> Our Contact Page </h2>
    <div class="container  px-lg-5">
        <form @submit="handleForm">
            <div class="row p-lg-5 mx-lg-5 from_box alert-secondary ">
                <div class="col-12">
                    {{ formdata.fname.toUpperCase() }} {{ formdata.lname }} {{ formdata.email }} {{ formdata.mobile_num
                    }}
                    <br> {{ formdata.message }} {{ formdata.cheked_names }} {{ formdata.gender }}
                </div>
                <div class="col-lg-6">
                    <label class="w-100"> Enter First Name </label>
                    <input type="text" name="firstname" id="fname" class="form-control" 
                    @input="req_uired"
                    @blur="req_uired" @keypress="isLetter($event)" v-model="formdata.fname"
                    :style="error.firstname.state ? 'border-color:red' : null" maxlength="12" />

                    <p v-if="alphaMsg" style="color:#ba0000;text-align: left"> {{ alphaMsg }} </p>
                    <p v-if="error.firstname.state" style="color:red; text-align: left;"> 
                        {{ error.firstname.message }} </p>


                </div>

                <div class="col-lg-6">
                    <label class="w-100">Enter Last Name </label>
                    <input type="text" class="form-control" v-model="formdata.lname" />
                </div>


                <div class="col-lg-6">
                    <label class="w-100">Enter email </label>
                    <input type="email" name="email" class="form-control" v-model="formdata.email" @input="req_uired"
                        @blur="req_uired" :style="error.email.state ? 'border-color:red' : null" />
                    <p v-if="error.email.state" style="color:red; text-align: left;"> {{ error.email.message }} </p>
                </div>

                <div class="col-lg-6">
                    <label class="w-100"> Enter Mobile Number </label>
                    <input type="number" id="mobile_num" class="form-control" v-model="formdata.mobile_num" />
                </div>

                <div class="col-lg-6   ">
                    <label class="w-100"> Select Quantity </label>
                    <select class="form-select" aria-label="Default select example">
                        <option selected>Open this select menu</option>
                        <option value="1">One</option>
                        <option value="2">Two</option>
                        <option value="3">Three</option>
                    </select>
                </div>



                <div class="col-lg-6  ">
                    <label class="ps-3">
                        <input type="checkbox" id="sing_ing" value="Singing" v-model="formdata.cheked_names" />
                        Singing
                    </label>
                    <label class="ps-3">
                        <input type="checkbox" id="sing_ing" value="Dancing" v-model="formdata.cheked_names" />
                        Dancing
                    </label>
                    <label class="ps-3">
                        <input type="checkbox" id="sing_ing" value="Reading" v-model="formdata.cheked_names" />
                        Reading
                    </label>
                </div>

                <div class="col-lg-6  text-start">
                    <label class="ps-3">
                        <input id="male" name="gender" type="radio" value="male" v-model="formdata.gender" />
                        Male
                    </label>
                    <label class="ps-3">
                        <input id="fe_male" name="gender" type="radio" value="female" v-model="formdata.gender" />
                        Female
                    </label>
                    <p v-if="formdata.gender == 'male'"> this will show when male selected </p>
                    <p v-else-if="formdata.gender == 'female'"> this will show when female selected </p>
                    <p v-else> this will show when nothing selected </p>

                </div>

                <div class="col-lg-12  mx-0">
                    <label class="w-100 text-start"> Write About You </label>
                    <textarea class="w-100" cols="60" rows="4" v-model="formdata.message"></textarea>

                </div>



                <div class="col-lg-12 py-2 ">
                    <button type="submit " class="btn btn-dark"> Submit Form </button>
                </div>

            </div>
        </form>

    </div>
</template>


<style>
.from_box .col-lg-6 label {
    margin-top: 1rem;
    text-align: left;
}
</style>

<script>
export default {
    name: "ConTact",

    data() {
        return {

            formdata: {

                fname: '',
                email: "",
                mobile_num: "",
                message: "",
                select_one: "",
                gender: '',
                cheked_names: []
            },
            error: {
                firstname: {
                    state: false,
                    message: ''
                },
                email: {
                    state: false,
                    message: ''
                }

            },
            alphaMsg: ''

        }
    },
    methods: {

        req_uired(e) {
            let value = e.target.value;
            let inptName = e.target.name;

            this.error[inptName] = {
                state: value ? false : true,
                message: value ? "" : "this field is Required"
            }

        },
        isLetter(e) {
            let char = String.fromCharCode(e.keyCode);
            if (/^[A-Za-z]+$/.test(char)) return true;
            else e.preventDefault();
            this.alphaMsg = "Only Alphabetics Allowed";
        },


        handleForm(e) {
            e.preventDefault();
            let form = JSON.stringify(this.formdata)
            let form_reslt = JSON.parse(form)
            console.log(form_reslt)
        }

    }

}

</script>