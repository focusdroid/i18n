<template>
  <div class="hello">
    <p>{{$t('message.hello')}}</p>
    <el-time-select
      v-model="value1"
      :picker-options="{
    start: '08:30',
    step: '00:15',
    end: '18:30'
  }"
      placeholder="选择时间">
    </el-time-select>
    <el-select v-model="switchsValue" @change="switchs" placeholder="请选择">
      <el-option
        v-for="item in switchsOptions"
        :key="item.value"
        :label="item.label"
        :value="item.value">
      </el-option>
    </el-select>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      value1: '',
      switchsOptions: [{
        value: 'cn',
        label: '中文'
      }, {
        value: 'en',
        label: '英文'
      }],
      switchsValue: ''
    }
  },
  created () {
    // localStorage.lang == undefined?'cn':localStorage.lang
  },
  methods: {
    switchs () {
      this.$i18n.locale = this.switchsValue
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
