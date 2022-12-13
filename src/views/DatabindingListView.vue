
<template>
    <div>
      <h2>hello</h2>
      <select name="" id="">
        <option value="" :key="list.code" :v-for="list in lists"></option>
      </select>
    </div>
</template>

<script>
export default {
    components: {},
    data() {
        return{
          lists: [
            {title:"서울", code:"02"}
            {title:"부산", code:"051"}
            {title:"제주", code:"064"}
          ]
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

</style>
