
<template>
  <div>
    <h2>{{ msg }}</h2>
  </div>

  <div>
    <el-row :gutter="2">
      <el-col :span="24"
        ><input
          type="file"
          id="upload-file"
          ref="userFile"
          @change="readFile()"
      /></el-col>
    </el-row>
    <el-row :gutter="10">
      <el-col :span="2" />
      <el-col :span="10">
        <el-input
          type="textarea"
          rows="18"
          id="text-input"
          placeholder="Paste your content here"
          v-model="userData"
        ></el-input>
      </el-col>
      <el-col :span="10">
        <el-input
          type="textarea"
          rows="18"
          id="formatted-output"
          placeholder="Here is the output"
          v-model="format"
        ></el-input>
      </el-col>
    </el-row>
  </div>
</template>

<style>
.el-row {
  margin-bottom: 20px;
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 2px 0;
  background-color: #f9fafc;
}

.buttons {
  display: flex !important;
  align-items: center;
}
</style>

<script>
export default {
  name: "JsonFormatter",
  props: {
    msg: String,
  },
  data() {
    return {
      userData: "",
      outputData: "",
    };
  },
  methods: {
    readFile() {
      var cmp = this;
      var fr = new FileReader();
      fr.onload = function () {
        cmp.userData = fr.result;
      };

      fr.readAsText(this.$refs.userFile.files[0]);
    },
  },
  computed: {
    format() {
      if (this.userData != "") {
        try {
          var obj = JSON.parse(this.userData);
          return JSON.stringify(obj, null, 4);
        } catch (error) {
          return error;
        }
      }
      return "";
    },
  },
};
</script>