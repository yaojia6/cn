# 云硬盘API


## 简介
云硬盘API包含云硬盘相关接口和快照相关接口。可提供批量创建云硬盘，删除云硬盘，制作云硬盘快照等功能。


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**createDisks**|POST|-   创建一块或多块按配置或者按使用时长付费的云硬盘。</br>-   云硬盘类型包括高效云盘(premium-hdd)、SSD云盘(ssd)、通用型SSD(ssd.gp1)、性能型SSD(ssd.io1)、容量型HDD(hdd.std1)。</br>-   计费方式默认为按配置付费。</br>-   创建完成后，云硬盘状态为 available。</br>-   可选参数快照 ID用于从快照创建新盘。</br>-   批量创建时，云硬盘的命名为 硬盘名称-数字，例如 myDisk-1，myDisk-2。</br>-   maxCount为最大努力，不保证一定能达到maxCount。</br>|
|**createSnapshot**|POST|-   为指定云硬盘创建快照，新生成的快照的状态为creating。</br>-   同一地域下单用户快照的配额为15块。</br>-   为保证数据完整性，请您在创建快照之前，停止对云硬盘进行写入操作，以保证快照数据的完整性。</br>-   在执行创建快照前，建议您对云硬盘进行卸载操作，创建快照后再重新挂载到云主机上。</br>-   手动快照的生命周期独立于云硬盘，请您及时删除不需要的快照。</br>-   创建快照所需时间取决于云硬盘容量的大小，云硬盘容量越大耗时越长。</br>|
|**deleteDisk**|DELETE|-   删除一块按配置计费的云硬盘，云盘类型包括高效云盘、SSD云盘、通用型SSD、性能型SSD和容量型HDD。</br>-   删除云盘时，云盘的状态必须为 待挂载（Available）。</br>-   云盘被删除后，云硬盘快照可以被保留。</br>|
|**deleteSnapshot**|DELETE|-   删除单个云硬盘快照:快照状态必须为 available 或 error 状态。</br>-   快照独立于云硬盘生命周期，删除快照不会对创建快照的云硬盘有任何影响。</br>-   快照删除后不可恢复，请谨慎操作。</br>|
|**describeDisk**|GET|查询某一块云硬盘的信息详情|
|**describeDisks**|GET|-   查询您已经创建的云硬盘。</br>-   filters多个过滤条件之间是逻辑与(AND)，每个条件内部的多个取值是逻辑或(OR)</br>|
|**describeSnapshot**|GET|查询云硬盘快照信息详情|
|**describeSnapshots**|GET|查询云硬盘快照列表，filters多个过滤条件之间是逻辑与(AND)，每个条件内部的多个取值是逻辑或(OR)|
|**extendDisk**|POST|-   扩容云硬盘到指定大小，云硬盘状态必须为 available。</br>-   当云硬盘正在创建快照时，不允许扩容。</br>|
|**modifyDiskAttribute**|PATCH|修改云硬盘的名字或描述信息，名字或描述信息至少要指定一个。|
|**modifySnapshotAttribute**|PATCH|修改快照的名字或描述信息|
|**restoreDisk**|POST|-   仅可对制作快照的源硬盘进行数据恢复操作。</br>-   仅源硬盘处于可用状态时才能使用快照进行数据恢复操作。</br>-   云硬盘恢复后，当前数据将被清除，请您谨慎操作。</br>|