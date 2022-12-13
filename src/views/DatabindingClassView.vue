
<template>
    <div>
      <h2 :class="{'red-text':true}">Red Text</h2>
      <h2 :class="{'green-background':true}">green-background</h2>
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
    methods: {}
}
</script>

<style scoped>
.red-text{
  color: red;
}

.green-background{
  background: lawngreen;
  color: #fff;
}
</style>
