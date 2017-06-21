<style>

#map {
    min-height: 200px;
}

</style>

<template>

<div id="map-wrapper">
    <div id="map"></div>
    Map goes here
</div>

</template>

<script>

export default {
    name: 'mapwidget',
    props: {
        apikey: '',
        locationsrc: ''
    },
    data: function() {
        return {
            gmapLib: {},
            gmap: {}
        }
    },
    methods: {
        loadLocations: function(){
            // Grab a list of locations from a provided data source
        }
    },
    mounted: function() {
        let mapper = this;
        const loadGoogleMapsAPI = require('load-google-maps-api')
        let mapOptions = {
            "key": mapper.apikey
        };
        loadGoogleMapsAPI().then(function(googleMaps) {
            mapper.gmapLib = googleMaps;
        }).catch((err) => {})
    },
    watch: {
        gmapLib: function() {
            let mapper = this;
            console.dir(mapper.gmapLib);
            mapper.gmap = new mapper.gmapLib.Map(document.getElementById('map'), {
                center: {
                    lat: -34.397,
                    lng: 150.644
                },
                scrollwheel: false,
                zoom: 8
            });
        }
    }
}

</script>
