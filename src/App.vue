<template>
  <div class="form_container">
    <div class="form_example">
      <h3>Input data form</h3>

      <form @submit.prevent="processData">
        <div class="form_control">
          <label for="text">text</label>
          <input type="text" name="text" v-model="FormData.text">
        </div>
        <div class="form_control">
          <label for="radio">radio</label><br>
          A<input type="radio" name="radio" v-model="FormData.radio" value="A"><br>
          B<input type="radio" name="radio" v-model="FormData.radio" value="B"><br>
          C<input type="radio" name="radio" v-model="FormData.radio" value="C"><br>
        </div>
      
      <div class="form_control">
        <label for="longText">checkbox</label>
        <textarea name="longText" v-model="FormData.longText" />
      </div><br>
      <div class="form_control">
        <labe for="select">Frutas:</labe>
        <select name="select" v-model="FormData.select">
          <option value="" select>---selecciona---</option>
          <option value="patatas">patatas</option>
          <option value="manzanas">manzanas</option>
          <option value="peras">peras</option>
        </select>
      </div><br>
      <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">Enviar</button>
    </form>
    </div>
    <div class="form_output">
      <h3>Output data form</h3>
      <pre>{{ FormData }}</pre>
    </div>
  
  </div>
</template>

<script>
export default {
  // config del component
  data() {
    return {
      FormData: {
        text: "Juan",
        longText: "Carlos",
        checkbox: true,
        radio: "A",
        select: ""
      }

    }
  },
  methods:{
    processData(){
      alert(JSON.stringify(this.FormData))
    }
  }

}

</script>

<style lang="sass" scoped>
.form_container
  @apply min-h[200px] flex gap-4 mx-auto max-w-5xl w-11/12
  h3 
    @apply font-bold mb-4
  .form_example
    @apply flex-1
    .form_control
      @apply flex flex-col gap-2 mb-4
 

</style>
