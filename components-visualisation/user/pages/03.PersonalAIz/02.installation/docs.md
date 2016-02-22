---
title: Installation
taxonomy:
    category: docs
---

The PersonalAIz Platform is being delivered

##### Installation Process:

**Step 1: **Download docker container from github:

```html
http://github.org/yds/personalaiz_docker.tar.gz
````

**Step 2: **Unzip file.

**Step 3: **Load docker image on docker:

```html
docker load -i /path/personalaiz_docker.tar
````

**Step 4: **Run PersonalAIz Docker image and bind export port to 50001:

```html
docker run --hostname="pserver" -it --rm -p 50001:50001 ncsr/personalaiz:0.2 /bin/bash
````

**Step 5: **Start container services by executing start-service.sh:
```html
/opt/start-services.sh
````

**Step 6: **Import PersonalAIz DB schema in HBase storage:
```html
/opt/hbase/bin/hbase shell /opt/pserver_hbase_schema.txt
````

**Step 7: **Run "list" command to see the generated schema:
```html
list
````
![List output](/user/images/hbaseList.jpg)

**Step 8: **Exit from HBase shell by typing exit:
```html
exit
````

**Step 9: **Detach from the Docker container by typing Ctrl+P+Q

**Step 10: **Initialize PersonalAIz platform by visiting on browser:

>>>>> Change rootPassword with your desired password

```html
http://localhost:50001/PersonalAIz/api/pserver/root|root/admin/initialization/rootPassword
````

**Step 11: **Attempt to login with Username: root and Password: the one tha you defined on previous step:

>>>>> Change rootPassword with your desired password

```html
http://localhost:50001/PersonalAIz
````
