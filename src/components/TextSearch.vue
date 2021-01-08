<template>
  <div class="card" style="padding:20px;margin:15px">
    <div class="card-header">
      <h1>Users List</h1>
    </div>
    <div class="card-body">
      <div id="app">
          <VueBootstrap4Table :rows="rows" :columns="columns" :config="config">
          </VueBootstrap4Table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import VueBootstrap4Table from 'vue-bootstrap4-table'

export default {
  components: {
    VueBootstrap4Table
  },
  data() {
    return {
      rows: [],
      columns: [
      {
        label: "id",
        name: "id",
        sort: true,
      },
      {
        label: "Name",
        name: "name",
        sort: true,
      },
      {
        label: "Email",
        name: "email",
        sort: true,
      },
      {
        label: "Company",
        name: "company",
      },
      {
        label: "Phone",
        name: "phone",
      },
      {
        label: "Website",
        name: "website",
      }],
      config: {
          global_search: {
              placeholder: "Enter custom Search text",
              visibility: true,
              case_sensitive: false,
              searchDebounceRate: 1000,
              checkbox_rows: true,
              init: {
                  value : ""
              }
          },
      }
    }
  },
  methods: {
    init() {
      axios.get('https://jsonplaceholder.typicode.com/users').then((response) => {
        this.prepareData(response.data);
      })
    },
    prepareData(data) {
      data.forEach((i) => {
        this.rows.push(
          {
              "id": i.id,
              "name":i.name,
              "email": i.email,
              "company":i.company.name,
              'phone': i.phone,
              'website': i.website
          }
        );
      })
    }
  },
  mounted() {
    this.init()
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
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
