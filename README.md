# Neo4j-Admin Import

* insert data file .csv to server via FileZilla

<img width="591" alt="image" src="https://user-images.githubusercontent.com/110078907/181160672-2e254e80-d5cb-43fd-80af-aa5d0518c66e.png">

* connect your ssh/server 

![image](https://user-images.githubusercontent.com/110078907/181174431-40fbbdfa-2fa7-48d1-a7ff-50ee938ff512.png)

* go to path file /home/neo4j-enterprise-4.4.8 and create directory header for data file

* create script neo4j-admin import in your text editor

Example:

	./neo4j-admin import --database='Januari2021' --force --delimiter=',' --skip-duplicate-nodes --ignore-empty-strings --skip-bad-relationships --processors=6 \
	--nodes=Customer=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/node/cusinfo.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/customer/cusinfo_202101_final.txt \
	--nodes=Transaction=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/node/dm_transaction.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/transaction/awk_dm_transaction_20210101.txt \
	--relationships=send=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/rel/rel_send.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/transaction/awk_dm_transaction_20210101.txt \
	--relationships=receive=/home/arliputraa/neo4j-enterprise-4.4.10/import/header/rel/rel_receive.txt,/home/arliputraa/neo4j-enterprise-4.4.10/import/data/transaction/awk_dm_transaction_20210101.txt  


--nodes/relationships=<label>=<location path file header>,<location path file data>

* buat nodesnya

ubah file headeruser.csv menjadi:

id:ID(USER-ID),user_name,first_name,last_name,email,gender,age

ubah file header_interests.csv menjadi:

id:ID(INTEREST-ID),interest		

* buat relasinya

mkdir relation -> ls -> mv header_followers.csv header_people_interests.csv header_referrals.csv relation

ketik head header_followers.csv ,ubah atau buat relasinya seperti dibawah

from_id:START_ID(USER-ID),to_id:END_ID(USER-ID)

ketik head header_referrals.csv

from_id:START_ID(USER-ID),to_id:END_ID(USER-ID),referral_date

ketik head header_people_interests.csv

id:START_ID(USER-ID),int_id:END_ID(INTEREST-ID)


