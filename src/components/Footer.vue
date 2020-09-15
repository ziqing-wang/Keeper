<template>
  <div>
    <footer>
      <p>Copyright ⓒ {{year}}</p>
    </footer>
  </div>
</template>

<script>
export default {
    data(){
        return {
            year: new Date().getFullYear()
        }
    }
}
</script>

<style scoped>
footer{
    position: absolute;
    bottom: 0;
    left: 45%;
}
</style>