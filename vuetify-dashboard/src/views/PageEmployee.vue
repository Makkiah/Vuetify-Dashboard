<template>
	<div>
		<h1>Dashboard</h1>
		<v-data-table
			:headers="headers"
			:items="employees"
			:items-per-page="5"
			class="elevation-1"
			@click:row="selectRow"
			:multi-sort="true"
		></v-data-table>

        <ProductTabs/>
        <!-- Two Imported Components, Different declaration -->
        <ProductReview/>
        <toggle-class></toggle-class>

        <!-- Snackbar -->
		<v-snackbar v-model="snackbar">
			You have selected {{ selectedEmployee.name }},
			{{ selectedEmployee.title }}
			<v-btn color="pink" text @click="snackbar = false">
				Close
			</v-btn>
		</v-snackbar>
	</div>
</template>

<script>
import employeesData from '../data/employeesData.json'
import ProductReview from '@/components/ProductReview.vue'
import ToggleClass from '@/components/ToggleClass.vue'
import ProductTabs from '@/components/ProductTabs.vue'

export default {
	name: 'DashboardPage',
    components: {
        ProductReview,
        ToggleClass,
        ProductTabs
    },
	data() {
		return {
			selectedEmployee: {
				name: '',
				title: ''
			},
			headers: [
				{ text: 'Employee ID', value: 'id' },
				{ text: 'Name', value: 'name' },
				{ text: 'Position Title', value: 'title' },
				{ text: 'Salary', value: 'salary' }
			],
            snackbar: false,
			employees: employeesData
		}
	},
	methods: {
		selectRow(event) {
			this.snackbar = true
			this.selectedEmployee.name = event.name
			this.selectedEmployee.title = event.title
		}
    }
}
</script>

<style>
    .center{
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 5px auto;
    }
</style>