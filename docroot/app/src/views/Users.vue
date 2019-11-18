<template>
  <div>
    <h2>Users list</h2>

    <div v-if="!users.length" class="alert alert-warning">
      Loading...
    </div>

    <user-list v-else :users="users" />
  </div>
</template>

<script>
import axios from 'axios'
import UserList from '@/components/UserList.vue'

export default {
  name: 'UsersPage',
  components: {
    'user-list': UserList
  },
  data: () => ({
    users: []
  }),
  mounted() {
    this.loadData()
  },
  methods: {
    loadData() {
      axios.get('http://localhost:3004/users').then(({ data }) => {
        this.users = data
      })
      // .catch(error => console.error(error))
    }
  }
}
</script>
