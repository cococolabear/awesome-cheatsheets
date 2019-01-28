## 查询commit最多的次数类

echo '' > /tmp/11.txt
for i in `ls| grep -v 1.sh`
do
  PROJECT_NAME=${i}
  cd ${i}
  for j in `find . -type f|grep java`
  do
    # echo ${j}
    CHANGE_COUNT=`git log --pretty=oneline ${j} | wc -l`
    FILEANME=`basename ${j}`
    echo "${PROJECT_NAME} ${FILEANME} ${CHANGE_COUNT}" >> /tmp/11.txt
  done
  cd ..
done

cat /tmp/11.txt |  awk '{print $3" "$1" "$2}'| sort -nr | head -10
