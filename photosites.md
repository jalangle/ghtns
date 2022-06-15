---
category: Photography
description: interesting photography locations
include: true
layout: category
title: Photo Sites
permalink: /photosites/
---

<!--
<style>
  #map {
   height: 400px;
   width: 100%;
   overflow: hidden;
   float: left;
   border: thin solid #333;
   }
</style>
<div id="map"></div>
<div id="capture"></div>
<script>
  var map;
  var src = '{{site.url}}/photosites/sites.kml';

  function initMap() {
    map = new google.maps.Map(document.getElementById('map'), {
      center: new google.maps.LatLng(47.601927, -122.338229),
      zoom: 2,
      mapTypeId: 'terrain'
    });

    var kmlLayer = new google.maps.KmlLayer(src, {
      suppressInfoWindows: true,
      preserveViewport: false,
      map: map
    });
    kmlLayer.addListener('click', function(event) {
      var content = event.featureData.infoWindowHtml;
      var testimonial = document.getElementById('capture');
      testimonial.innerHTML = content;
    });
  }
</script>
<script async
src="https://maps.googleapis.com/maps/api/js?key=AIzaSyCVeQCLZtsZYDKOPqtX7tkNII3qYjPiNME&callback=initMap">
</script>
-->

## Sites

{% for photosite in site.photosites %}
### [{{photosite.title}}]({{site.baseurl}}{{photosite.url}})

{% endfor %}

