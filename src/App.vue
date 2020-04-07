<template>
  <div id="app">
    <download-excel
      class="btn btn-default"
      :data="json_data"
      :fields="json_fields"
      worksheet="My Worksheet"
      name="filename.xls"
    >Download Excel (you can customize this with html code!)</download-excel>
  </div>
</template>
<script>
export default {
  data() {
    return {
      json_fields: {
        "Complete name": "name",
        City: "city",
        Telephone: "phone.mobile",
        "Telephone 2": {
          field: "phone.landline",
          callback: value => {
            return `Landline Phone - ${value}`;
          }
        }
      },
      json_data: [
        {
          name: "Tony Peña",
          city: "New York",
          country: "United States",
          birthdate: "1978-03-15",
          phone: {
            mobile: "1-541-754-3010",
            landline: "(541) 754-3010"
          }
        },
        {
          name: "Thessaloniki",
          city: "Athens",
          country: "Greece",
          birthdate: "1987-11-23",
          phone: {
            mobile: "+1 855 275 5071",
            landline: "(2741) 2621-244"
          }
        }
      ],
      json_meta: [
        [
          {
            key: "charset",
            value: "utf-8"
          }
        ]
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
