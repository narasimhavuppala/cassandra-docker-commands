# cassandra-docker-commands

	docker run --name=n1 -d tobert/cassandra
	docker inspect -f '{{ .NetworkSettings.IPAddress }}' n1
	docker run --name=n2 -d tobert/cassandra -seeds IP
	docker run --name=n3 -d tobert/cassandra -seeds IP
	docker exec -it n1 nodetool status
	docker exec -it n1 nodetool ring
	docker exec -it n1 /bin/bash vi /data/conf/cassandra.yaml
	docker stop n1 n2 n3
	docker rm n1 n2 n3



To deploy a single Cassandra node, specifying a datacenter and rack:

	docker run --name n1 -d tobert/cassandra -dc DC1 -rack RAC1
	docker run --name n1 -d tobert/cassandra -dc DC1 -rack RAC2 -seeds IP

 To add a third node in a different datacenter:

 	docker run --name n3 -d tobert/cassandra -dc DC2 -rack RAC1 -seeds IP

 	(where again the IP is the IP address retrieved previously)

To view the configuration file where the datacenter and rack info is stored:

	docker exec -it n1 /bin/bash
	vi /data/conf/cassandra-rackdc.properties



