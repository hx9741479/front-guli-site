<template>
  <div>
    讲师列表
    <div v-for="(item,index) in items" :key="index">
      <a :href="'teacher/'+item.id">{{ item.name }}</a>
    </div>
    <p>{{ test }}</p>
  </div>
</template>
<script>
import teacherApi from '~/api/teacher'
export default {
  // 异步获取数据
  async asyncData() {
    console.log('asyncData')
    const response = await teacherApi.getList()
    console.log(response)
    return {
      items: response.data.items
    }
  },

  data() {
    return {
      test: 'testafsd' // 这里的数据最后会和asyncData中的数据定义合并
    }
  }
}
</script>
