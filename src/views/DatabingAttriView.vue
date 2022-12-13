
<template>
    <div>
      <input @keyup.="myFunc">
    </div>
</template>

<script>
export default {
    components: {},
    data() {
        return{

        }
    },
    setup() {},
    created() {},
    mounted() {},
    unmounted() {},
    methods: {
      myFunc() {
        alert("hello!!")
      }
    }
}
</script>

<style scoped>

</style>
