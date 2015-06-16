---
layout: default
title: Travel Map
---

<div class="post">
	<h1 class="pageTitle">Travel Map</h1>
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

	</script>

</div>
