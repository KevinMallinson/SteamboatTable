<template>
	<table>
		<thead>


		<tr>
			<th v-for="key in columns" :key="key.key"> 
				{{key.label ? key.label : key.key}}
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
					return Object.keys(this.renderedItems[0]);
				} else {
					return this.columns.map(x => x.key);
				}
			}
		}
	}
</script>

<style lang="scss">
	table {
		border-collapse: collapse;
		margin: 0px;
	}

	table, th, td {
		border: 1px solid black;
	}
</style>
