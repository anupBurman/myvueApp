<template>
    <div class="foo_tr">
        <h3> This is Footer Section </h3>
        <button class="btn btn-sm btn-dark" @click="addd()"> Click to Result </button>
        <h2 v> Result is = {{ result }} </h2>
    </div>
    
</template>

<script>
export default {
   name: "FooTer",
   data() {
    return {
        a: 5,
        b: 7,
        c: 4,
        result: ""

    }
   },
   methods:{
    addd(){
        let result = this.a+this.b;
        this.result = result*this.c;
    }
   }
}
</script>

