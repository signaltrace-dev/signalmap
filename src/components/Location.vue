<style>

.location-tile {
    min-height: 10px;
}

</style>

<template>

<div class="location location-tile">
    The location details
</div>

</template>

<script>

export default {
    name: 'location',
    props: {
        locationid: ''
    },
    data: function() {
        return {
            lat: '',
            lng: '',
            addressLine1: '',
            addressLine2: '',
            city: '',
            state: '',
            zip: '',
            url: '',
            phone: '',
            name: '',
            description: ''
        }
    },
    methods: {

    },
    mounted: function() {
        var location = this.$parent.getLocation(this.locationid);
        for(var propertyName in location) {
            this[propertyName] = location[propertyName];
        }
    },
    watch: {
    }
}

</script>
