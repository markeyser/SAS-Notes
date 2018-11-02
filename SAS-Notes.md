### Get first observations by group
Let's sort by GO code;
```
proc sort data = lise.agt_geo_sls_addr out=work.agt_geo;
	by ou_cd;
run;
```
Now let's take the first observation per GO code
```
data agt_geo_single;
	set agt_geo_v01;
	by ou_cd;
	if first.ou_cd then output agt_geo_single;
run;
```
### Left Join using using `PROC SQL`
```
proc sql;
	create table work.agent_type_02 
	as select a.*, b.fyc_prior as prior_fyc
	from work.agent_type_01 a 
	left join lise.marcos_agt_lic b 
	on a.agt_num=b.mk_id;  
quit;
``` 
### Listing variables using `PROC CONTENTS`
Listing the variables. The 	`varnum` and `nodetails`
```
proc contents data=agt_goe_v02 varnum nodetails;
run;
```
dfdsfdffsad
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDA0OTc4MjMsLTEzNTEyNzI5ODAsMT
g0NTY0NzY2OSwtMTg2NDI4MTE5LDExODY1MTUzODcsLTE0NDA2
MDA5NTldfQ==
-->