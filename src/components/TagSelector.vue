<template>
  <div class="Menu">
    <div v-for="(language, index) in languages" 
    :key="index"
    @click="language.selected =! language.selected"
    :class="{selected: language.selected}"
    >
        <span>{{language.name}}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      languages: [
        { name: "php", selected: false },
        { name: "js", selected: false },
        { name: "java", selected: false },
        { name: "c", selected: false },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.Menu div{
    display: inline-block;
    border: 1px solid blue;
    padding: 5px 15px;
    margin-right: 5px;
    border-radius: 5px;
}
.Menu div.selected{
    background-color: red;
    color: #fff;
}
</style>
