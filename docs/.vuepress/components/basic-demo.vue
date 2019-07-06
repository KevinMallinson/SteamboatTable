<template>
    <div>
        <p>
            The following is an example of Steamboat Table in its purest form.
            It has no properties being used apart from the mandatory `items`.
            `items` is an object of the rows, which must all have the same properties.
        </p>
        <steamboat-table :items="items"/>
    </div>
</template>

<script>
import SteamboatTable from '../../src/SteamboatTable'

export default {
    components: {
        SteamboatTable
    },
    data() {
        return {
            items: [{
                firstName: 'John',
                lastName: 'Doe',
                age: '34',
                occupation: 'Web Developer'
            }, {
                firstName: 'Jane',
                lastName: 'Doe',
                age: '22',
                occupation: 'Marketing'
            }, {
                firstName: 'Bill',
                lastName: 'Thompson',
                age: '37',
                occupation: 'Human Resources'
            }]
        }
    }
}
</script>

<style>

</style>
