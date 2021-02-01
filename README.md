# docker 部署elk

## 运行

### 创建容器网络
 - docker networks create elk_net
 - 修改kibana.server.host配置
 - docker-compose up -d 
 
## 问题说明

### ES 部署问题

 - 问题1：java.nio.file.AccessDeniedException: /usr/share/elasticsearch/data/nodes 
 - 处理：在相关目录上执行 chown -R user:user data, user-> 非root用户
    
 - 问题2：bootstrap checks failed
 - 原因：Swapping needs to be disabled for performance and node stability. For information about ways to do this
 - 处理：修改docker-compose.yml 增加配置"bootstrap.memory_lock=false"
 
 - 问题3：max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
 - 原因：最大虚拟内存太小,需要修改系统变量的最大值
 - 处理：执行 sudo sysctl -w vm.max_map_count=262144























