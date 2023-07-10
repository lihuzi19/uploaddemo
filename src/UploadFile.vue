<script setup>

// export default {
//   methods:{
//     uploadFile() {
//       console.log("click uploadFile")
//     },
//   }
// }
</script>

<template>
  <div>
    <input v-show="false" ref="fileRef" type="file" @change="fileChange">
    <el-row>
      <el-button type="primary" @click="uploadFile">警告按钮</el-button>
    </el-row>
  </div>
</template>

<style scoped>

</style>

<script>
import axios from "axios";

export default {
  methods: {
    uploadFile() {
      console.log("upload file method")
      this.$refs.fileRef.dispatchEvent(new MouseEvent('click'))
    },
    fileChange(event) {
      console.log(event.target.files[0])
      const file = event.target.files[0]
      const formData = new FormData()
      formData.append('file', file)
      fetch('/api/uploadFile', {
        method: 'POST',
        body: formData,
      }).
      then((response) => response.text()).
      then((data) => {
            console.log(data);
          })
    },
    getHello() {
      fetch("/api/hello",{
        method: "GET",
      }).
      then((response) => response.text()).
      then((data) => {
        console.log("getHello" + data);
      })
    },
  }
}
</script>


