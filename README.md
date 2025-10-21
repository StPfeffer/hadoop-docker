```
cd ~/hadoop
cd /your_project
mvn clean compile
cd ..
cp your_data.csv ./data/
cp your_project/target/YourJar-uber.jar ./data/
```

```
docker compose up -d
docker exec -it hadoop-resource-manager-1 bash

hdfs dfs -mkdir -p /input /output
hdfs dfs -put /data/your_data /input
hadoop jar /data/YourJar.jar /input/your_data.csv /output/result_$(date +%s)
```

```
hdfs dfs -cat /output/result_<TIMESTAMP>/part-r-00000
```
