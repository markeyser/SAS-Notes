### Get first observations by group
Let's sort by GO code;
````
proc sort data = lise.agt_geo_sls_addr out=work.agt_geo;
	by ou_cd;
run;
````
Now let's take the first observation per GO code
````
data agt_geo_single;
	set agt_geo_v01;
	by ou_cd;
	if first.ou_cd then output agt_geo_single;
run;
````
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NDA2MDA5NTldfQ==
-->