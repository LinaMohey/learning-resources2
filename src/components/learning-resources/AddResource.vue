<template>


  <form>

    <div>
    <label for="title"> Title</label>
    <input type="text" id="title" name="title" ref="titleInput">
  </div>

  <div>
    <label for="description"> Description</label>
    <textarea id="description" name="description" rows="3"  ref="descInput"> </textarea>
  </div>

  <div>
    <label for="link"> link</label>
    <input type="url" id="link" name="link"  ref="linkInput" >
  </div>
 <button @click="submitData">
Add resource
  </button>
    </form>


</template>



<script>
  export default {
    inject:['addResource'],
    methods:{
      submitData(){
        const enteredTitle= this.$refs.titleInput.value
        const enteredDesc= this.$refs.descInput.value
        const enteredUrl= this.$refs.linkInput.value

        this.addResource(enteredTitle,enteredDesc,enteredUrl)


      }


    }

  }
</script>

<style lang="scss" scoped>

</style>