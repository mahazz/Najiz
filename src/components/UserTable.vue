<template>
    <div>
    <div class="table-wrapper">
            <b-modal id="modal-1" title="Confirm" v-model="openDialog" ok-title="Remove" @ok="removeRowsHandler(id)">
        <p class="my-4">Are you sure you want to remove the selected rows?</p>
      </b-modal>
              <table class="table">
                <thead>
                  <th>
                    <div class="mobile-th">
                      <span class="label">رقم الطلب</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">نوع الطلب</span>
                    </div>
                  </th>

                  <th>
                    <div class="mobile-th">
                      <span class="label">نوع السند</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">تاريخ تقديم الطلب</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">المحكمة</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">طالب التنفيذ</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">المنفذ ضده</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">حالة الطلب</span>
                    </div>
                  </th>
                  <th>
                    <div class="mobile-th">
                      <span class="label">الاجراءات</span>
                    </div>
                  </th>
                </thead>
                <tbody>
                  <tr v-for="user in users" :key="user.id">
                    <!-- <td>
                    <b-checkbox  v-if="user.key === 'selectRow'" :checked="users[user.id].isSelected" :key="id" @change="selectRowHandler(user)"></b-checkbox>
                    <b-checkbox  v-if="user.key === 'selectRow'" :checked="users[data.id].isSelected" @change="selectRowHandler(data)"></b-checkbox>
                    <b-checkbox  v-if="user.key === 'selectRow'" :checked="users[user.id].isSelected" @change="selectRowHandler(user)"></b-checkbox>
                  </td> -->
                    <td>
                      <span>
                        <span class="label">{{ user.requestNumber }}</span>
                      </span>
                    </td>
                    <td>
                      <span>
                        <span class="label">{{ user.requestType }}</span>
                      </span>
                    </td>
                    <td>
                      <span>
                        <span class="label">{{
                          user.type
                        }}</span>
                      </span>
                    </td>
                    <td>
                      <span>
                        <span class="label">{{ user.requestDate }}</span>
                      </span>
                    </td>
                      <td>
                      <span>
                        <span class="label">{{ user.m }}</span>
                      </span>
                    </td>
                    <td>
                      <span>
                        <span class="label">{{ user.requestedBy}}</span>
                      </span>
                    </td> 
                    <td>
                      <span>
                        <span class="label">{{ user.requestedfor}}</span>
                      </span>
                    </td>
                    <td>
                      <span>
                        <span class="label">{{ user.requestStatus}}</span>
                      </span>
                    </td>
                    <td>
                      <b-button variant="danger" @click="removeRow(user.id)">اسقاط الوكالة عن هذا الطلب</b-button>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
    </div>
</template>

<script>
    import UsersData from '../UsersData'

    export default {
        name: "UserTable",
        data() {
    return {
      users: UsersData,
      openDialog: false
    };
  },
    methods: {
      removeRow(id) {
      this.users = this.users.filter(user => user.id !== id);
    },
    // selectRowHandler(user) {
    //     this.users[user.id].isSelected = !this.users[user.id].isSelected;
    //   },
    removeRowHandler(id) {
      this.users = this.users.filter((user, i) => i !== id);
      this.$emit("td", this.users);
      this.$emit("remove", this.users[id]);
    },
    removeRowsHandler() {
      const selectedUsers = this.users.filter((user) => user.isSelected);
      this.users = this.users.filter((user) => !user.isSelected);
      this.$emit("td", this.users);
      this.$emit("remove", selectedUsers);
    },
    selectRowHandler(user) {
  this.users[user.id].isSelected = !this.users[user.id].isSelected;
}
    },
  
    }
</script>

<style lang="scss">
  .action-container {
        margin-bottom: 10px;
    }
    .action-container button {
        margin-right: 5px;
    }
    .delete-button {
        margin-left: 5px;
    }

</style>