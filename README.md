(
  avg(ibm_databases_for_redis_disk_used_bytes{ibm_resource_group_name="rg-ec002i002948"})
  /
  avg(ibm_databases_for_redis_disk_total_bytes{ibm_resource_group_name="rg-ec002i002948"})
) * 100 > 80
