<template>
    <div>
        <div class="container mt-3">
            <h2>Toggleable Tabs</h2>
            <br>
            <!-- Nav tabs -->
            <ul class="nav nav-tabs" role="tablist">
                <li class="nav-item">
                    <a class="nav-link active" data-bs-toggle="tab" href="#home">Home</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" data-bs-toggle="tab" href="#menu1">Menu 1</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" data-bs-toggle="tab" href="#menu2">Menu 2</a>
                </li>
            </ul>

            <!-- Tab panes -->
            <div class="tab-content">
                <div id="home" class="container tab-pane active"><br>
                    <h3>HOME</h3>
                    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut
                        labore et dolore magna aliqua.</p>
                </div>
                <div id="menu1" class="container tab-pane fade"><br>
                    <h3>Menu 1</h3>
                    <p>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
                        consequat.</p>
                </div>
                <div id="menu2" class="container tab-pane fade"><br>
                    <h3>Menu 2</h3>
                    <p>Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium,
                        totam rem aperiam.</p>
                </div>
            </div>
        </div>


        <h2> About Us </h2>
        <!-- toggle example on click  -->
        <button class="btn btn-sm btn-dark" @click="show = !show"> show More </button>
        <div v-if="show">
        </div>
        <h5 v-else>
            This is Else Part
        </h5>


        <h4> Wellcome {{ userId }} </h4>
        <h6 v-for="(data, index) in content" :key="index"> {{ data }} </h6>
        <ul>
            <li v-for="(value, key, index ) in object" :key="index">
                {{ index + 1 }}. {{ key }} - {{ value }}
            </li>
        </ul>
        <button class="btn btn-danger" @click="updateMe()"> Click me </button>
    </div>
</template>

<script>


export default {
    name: "AboutUs",

    data() {
        return {
            userId: "0078",
            content: [
                "saurabh",
                "Anup",
                "Manish"
            ],
            object: {
                name: "Sonu",
                mobilenumber: "9977382633",
                Address: "Ward no.11, Mana-Camp, Raipur"
            },
            show: true
        }

    },


    methods: {
        // function 
        updateMe() {
            alert("hjhjh")
        }

    }
}


</script>
<style>
     .nav-tabs .nav-link.active{
        background-color: wheat !important;
    }
</style>
