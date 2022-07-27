# step-admin-import

* drag file ke FileZilla

sebelumnya masukkan ip/host, Username, password, dan port kemudian Quickconnect

<img width="591" alt="image" src="https://user-images.githubusercontent.com/110078907/181160672-2e254e80-d5cb-43fd-80af-aa5d0518c66e.png">

* masuk ke terminal

cara connect ssh "ssh ddi@192.168.18.115" password "...."

![image](https://user-images.githubusercontent.com/110078907/181174431-40fbbdfa-2fa7-48d1-a7ff-50ee938ff512.png)

* masuk ke directory neo4j (command: cd namadirectory) -> buat directory header 

head -1 namafileyangingindirubah.csv > /home/ddi/neo4j-enterprise-4.4.8/import/data_bank/header/file baru header_.csv

* pindahkan ke directory header

buat directory dahulu (command: mkdir header)

selanjutnya mv header_yangingindipindahin.csv headertutut.csv header (tidak pakai',')

* liat file path data (commad: pwd)

liat file path header/ file baru.csv (command: pwd)

* buat script admin import

./neo4j-admin import --database=sosmed --force --delimiter="," --skip-duplicate-nodes --multiline-fields=true --skip-bad-relationships=True --bad-tolerance=40000 --cache-on-heap --skip-bad-entries-logging --ignore-empty-strings \

--nodes=user=/home/ddi/neo4j-enterprise-4.4.8/import/data/header/headeruser.csv,/home/ddi/neo4j-enterprise-4.4.8/import/data/users.csv \

--nodes=interests=/home/ddi/neo4j-enterprise-4.4.8/import/data/header/header_interests.csv,/home/ddi/neo4j-enterprise-4.4.8/import/data/interests.csv \

--relationships=People_Interests=/home/ddi/neo4j-enterprise-4.4.8/import/data/header/relation/header_people_interests.csv,/home/ddi/neo4j-enterprise-4.4.8/import/data/people_interests.csv \

--relationships=Has_Follow=/home/ddi/neo4j-enterprise-4.4.8/import/data/header/relation/header_followers.csv,/home/ddi/neo4j-enterprise-4.4.8/import/data/followers.csv \

--relationships=Refferals=/home/ddi/neo4j-enterprise-4.4.8/import/data/header/relation/header_referrals.csv,/home/ddi/neo4j-enterprise-4.4.8/import/data/referrals.txt \

		nama nodes=path file header/filebaru.csv,file path data.csv

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


