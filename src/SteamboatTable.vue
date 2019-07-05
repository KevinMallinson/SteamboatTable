<template>
	<table>
		<thead>


		<tr>
			<th v-for="key in keys" :key="key.key"> 
				<template v-if="key.label || key.key">
					{{key.label ? key.label : key.key}}
				</template>
				<template v-else>
					{{key}}
				</template>
			</th>
		</tr>
		</thead>


		<tbody>
			<tr v-for="(item, index) in items" :key="index">
				<template v-for="itemKey in Object.keys(item)"> 
					<td v-if="keys.includes(itemKey)" :key="itemKey">
						<slot :name="itemKey" v-bind:item="item">
							{{item[itemKey]}}
						</slot>
					</td>
				</template>
			</tr>
		</tbody>


  </table>

</template>

<script>
	export default {
		props: {
			items: {
				required: true,
				type: Array
			},
			filter: {
				required: false,
				type: Function
			},
			columns: {
				required: false,
				type: Array
			}
		},
		computed: {
			keys() {
				if (!this.columns) {
					return Object.keys(this.items[0]);
				} else {
					return this.columns.map(x => x.key);
				}
			}
		}
	}
</script>

<style>
	table {
		border-collapse: collapse;
	}

	th, td {
		border: 1px solid black;
	}
</style>
