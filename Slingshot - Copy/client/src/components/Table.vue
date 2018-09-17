<template>
<v-app>
  <a id="customXLSXButton" class="waves-effect waves-light btn-flat"><img src="https://png.icons8.com/color/50/000000/ms-excel.png" v-on:click="downloadCSV()" style="height:25px; margin-top: 4px"></a>
  <v-data-table
      :headers="headers"
      :items="desserts"
      hide-actions
      class="elevation-1"
    >
      <template slot="items" slot-scope="props">
        <tr>
          <td>{{ props.item.name }}</td>
          <td class="text-xs-right">{{ props.item.calories }}</td>
          <td class="text-xs-right">{{ props.item.fat }}</td>
          <td class="text-xs-right">{{ props.item.carbs }}</td>
          <td class="text-xs-right">{{ props.item.protein }}</td>
          <td class="text-xs-right">{{ props.item.iron }}</td>
        </tr>
      </template>
    </v-data-table>
  </v-app>
</template>
 
<script>
/* eslint-disable */
import Papa from 'papaparse'

export default {
    name: 'tabletest',
    data() {
        return {
            tablename: 'RookieRumble',
            headers: [{
                    text: 'Dessert (100g serving)',
                    align: 'left',
                    sortable: false,
                    value: 'name'
                },
                {
                    text: 'Calories',
                    value: 'calories'
                },
                {
                    text: 'Fat (g)',
                    value: 'fat'
                },
                {
                    text: 'Carbs (g)',
                    value: 'carbs'
                },
                {
                    text: 'Protein (g)',
                    value: 'protein'
                },
                {
                    text: 'Iron (%)',
                    value: 'iron'
                }
            ],
            desserts: [{
                    value: false,
                    name: 'Frozen Yogurt',
                    calories: 159,
                    fat: 6.0,
                    carbs: 24,
                    protein: 4.0,
                    iron: '1%'
                },
                {
                    value: false,
                    name: 'Ice cream sandwich',
                    calories: 237,
                    fat: 9.0,
                    carbs: 37,
                    protein: 4.3,
                    iron: '1%'
                }
            ]
        }
    },
    mounted() {
        this.convertCSV()
    },
    methods: {
        convertCSV: function() {
            let b = Papa.unparse(this.desserts)
            return b
        },
        downloadCSV: async function() {
            let csv = await this.convertCSV()
            var blob = new Blob([csv]);
            if (window.navigator.msSaveOrOpenBlob) // IE hack; see http://msdn.microsoft.com/en-us/library/ie/hh779016.aspx
                window.navigator.msSaveBlob(blob, this.tablename + ".csv");
            else {
                var a = window.document.createElement("a");
                a.href = window.URL.createObjectURL(blob, {
                    type: "text/plain"
                });
                a.download = this.tablename + ".csv";
                document.body.appendChild(a);
                a.click(); // IE: "Access is denied"; see: https://connect.microsoft.com/IE/feedback/details/797361/ie-10-treats-blob-url-as-cross-origin-and-denies-access
                document.body.removeChild(a);
            }
        }
    }
}
</script>

<style>

table.v-table tbody td, table.v-table tbody th, table.v-table thead {
    height: 30px;
}

table.v-table thead tr {
    height: 30px;
}

tbody tr:first-child {
    background-color: lightblue;
    border: 0;
}

</style>