---
layout: default
title: Photo Map
---

<div class="post">
	<h1 class="pageTitle">Photo Map</h1>
	<p>Welcome to our world. The map will start centred on our most recent photograph. You can use your mousewheel or touchpad zoom control to zoom in to the map. Click, hold and drag on the map to pan around to find other photos across Europe. You can click any photo to see the larger version. To see all photos, visit <a href="https://instagram.com/thejimmydimple">my Instagram page</a>.</p>

	<div id="map" style="height: 800px"></div>
	<script src="lib/fancybox/jquery.fancybox.pack.js"></script>	
	<script src="lib/reqwest.min.js"></script>
	<script src="lib/leaflet/leaflet.js"></script>
	<script src="../dist/Leaflet.Instagram.Fancybox.js"></script>
	
	<script>
	var map = L.map('map').setView([-27.47, 153], 13);
	L.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token={accessToken}', {
    		attribution: 'Map data &copy; <a href="http://openstreetmap.org">OpenStreetMap</a> contributors, <a href="http://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="http://mapbox.com">Mapbox</a>',
   		maxZoom: 18,
    		id: 'thejimmydimple.a4929c55',
    		accessToken: 'pk.eyJ1IjoidGhlamltbXlkaW1wbGUiLCJhIjoiNTM3OWExOGJiODczN2QwYjNjNGY2ZjUwZTg0MTFiOTcifQ.okt3hntNx7jgsA0DcLz5OA'
	}).addTo(map); 

	L.instagram.fancybox('https://api.instagram.com/v1/users/33803954/media/recent?access_token=33803954.42e7a29.5f7d277e91a84278b9f229251a229544').addTo(map); 
	
	// bad solution: make another instagram query so we can get lat/long details...
	$.getJSON('https://api.instagram.com/v1/users/33803954/media/recent?callback=?', {
	count: 1,
	access_token: '33803954.42e7a29.5f7d277e91a84278b9f229251a229544' 
	}, function(resp) {
	$("#loading").hide();
	var markers = [];
	// set nice-ish zoom level
	map.setZoom(10, true);
	$.each(resp.data, function(k, inst) {
        // set the map view
        map.panTo([inst.location.latitude, inst.location.longitude], true, 1);
    	});
	});

	</script>

</div>
