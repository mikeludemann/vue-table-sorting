<template lang="html">

	<section class="table-sorting">
		<table :id="id">
			<tr> 
				<th v-for="dataHeader in dataTableHeader" @click="sortTable(dataHeader.id - 1)">{{dataHeader.name}}</th>
			</tr>
			<tr v-for="data in dataTable">
				<td>{{data.name}}</td>
				<td>{{data.country}}</td>
			</tr>
		</table>
	</section>

</template>

<script lang="js">

	export default {
		name: 'TableSorting',
		props: {
			id: {
				type: String
			},
			dataTable: {
				type: Array
			},
			dataTableHeader: {
				type: Array
			}
		},
		mounted () {

		},
		data () {
			return {

			}
		},
		methods: {
			sortTable: function(n) {
				var table, 
				rows, 
				switchChange, 
				i, 
				firstRow, 
				nextRow, 
				shouldSwitch, 
				direction, 
				switchcount = 0;

				table = document.getElementById(this.id);

				switchChange = true;
				direction = "asc"; 

				while (switchChange) {

					switchChange = false;

					rows = table.rows;

					for (i = 1; i < (rows.length - 1); i++) {

						shouldSwitch = false;

						firstRow = rows[i].getElementsByTagName("TD")[n];
							nextRow = rows[i + 1].getElementsByTagName("TD")[n];

						if (direction == "asc") {

							if (firstRow.innerHTML.toLowerCase() > nextRow.innerHTML.toLowerCase()) {

								shouldSwitch= true;
								break;

							}

						} else if (direction == "desc") {

							if (firstRow.innerHTML.toLowerCase() < nextRow.innerHTML.toLowerCase()) {

								shouldSwitch = true;
								break;

							}

						}

					}
					if (shouldSwitch) {

						rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
						switchChange = true;
						switchcount ++; 

					} else {

						if (switchcount == 0 && direction == "asc") {

							direction = "desc";
							switchChange = true;

						}

					}

				}

				}
		},
		computed: {

		}
}


</script>

<style scoped lang="scss">
	.table-sorting {

	}
</style>
