# Neo4j-Admin Import

* Insert data file .csv to server via FileZilla

<img width="591" alt="image" src="https://user-images.githubusercontent.com/110078907/181160672-2e254e80-d5cb-43fd-80af-aa5d0518c66e.png">

* Connect your ssh/server 

![image](https://user-images.githubusercontent.com/110078907/181174431-40fbbdfa-2fa7-48d1-a7ff-50ee938ff512.png)

* Go to path file /home/neo4j-enterprise-4.4.8 and create directory header for data file

* Create script neo4j-admin import in your text editor

Example:

	./neo4j-admin import --database='Januari2021' --force --delimiter=',' --skip-duplicate-nodes --ignore-empty-strings --skip-bad-relationships --processors=6 \
	--nodes=Customer=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/node/cusinfo.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/customer/cusinfo_202101_final.txt \
	--nodes=Transaction=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/node/dm_transaction.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/transaction/awk_dm_transaction_20210101.txt \
	--relationships=send=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/rel/rel_send.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/transaction/awk_dm_transaction_20210101.txt \
	--relationships=receive=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/rel/rel_receive.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/transaction/awk_dm_transaction_20210101.txt  

Description:

	--nodes/relationships=<label>=<location path file header>,<location path file data>

* Create ID for header Nodes
* Create START_ID and END_ID for header Relationships 

* Running script neo4j-admin import in path file neo4j/bin$


