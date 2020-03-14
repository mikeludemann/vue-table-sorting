<template>
	<div class="home">
		<img alt="Vue logo" src="../assets/logo.png">
		<HelloWorld msg="Welcome to Your Vue.js App"/>
		<TableSorting id="mainList" :dataTableHeader='[{ id: 1, name: "Name" }, { id: 2, name: "Country" }]' :dataTable='[{ id: 1, name: "John Doe", country: "Great Britain" },{ id: 2, name: "Mary Watson", country: "USA" },{ id: 3, name: "Dave Beck", country: "Ireland" },{ id: 4, name: "Brooke Tyson", country: "Italy" }]'></TableSorting>
	</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import TableSorting from '@/components/table-sorting.vue';

export default {
	name: 'Home',
	components: {
		HelloWorld,
		TableSorting
	}
}
</script>
