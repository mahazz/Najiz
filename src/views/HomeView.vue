<template>
  <div class="home">
    <div class="container">
      <div class="w-home">
        <h1 class="w-text">إدارة الوكلاء</h1>
        <button class="w-button">وكالات انت اصدرتها</button>
        <button class="w-button disabled" disabled="disabled">وكالات صادرة لك</button>
      </div>
     <div class="list">
      <h3 class="">قائمة الوكلاء الحاليين</h3>
      <p>اختر الوكيل لإستعراض الطلبات الموكل عليها</p>
      </div>
 <UserTable />
  </div>
  </div>
</template>

<script>
// @ is an alias to /src
import UserTable from '@/components/UserTable.vue'

export default {
  name: 'HomeView',
  components: {
    UserTable
  }
}
</script>
<style lang="scss">

.home {
        direction: rtl;
        text-align: justify;
      }
</style>
