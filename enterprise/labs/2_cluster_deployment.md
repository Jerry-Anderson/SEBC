http://ec2-75-101-204-230.compute-1.amazonaws.com:7180/api/v2/cm/deployment

```

  "timestamp" : "2016-09-21T18:26:13.593Z",
  "clusters" : [ {
    "name" : "Jerry-Anderson",
    "version" : "CDH5",
    "services" : [ {
      "name" : "hive",
      "type" : "HIVE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "HIVEMETASTORE",
          "items" : [ {
            "name" : "hive_metastore_java_heapsize",
            "value" : "2428502016"
          } ]
        }, {
          "roleType" : "HIVESERVER2",
          "items" : [ {
            "name" : "hiveserver2_java_heapsize",
            "value" : "2428502016"
          }, {
            "name" : "hiveserver2_spark_driver_memory",
            "value" : "966367641"
          }, {
            "name" : "hiveserver2_spark_executor_cores",
            "value" : "4"
          }, {
            "name" : "hiveserver2_spark_executor_memory",
            "value" : "3433247539"
          }, {
            "name" : "hiveserver2_spark_yarn_driver_memory_overhead",
            "value" : "102"
          }, {
            "name" : "hiveserver2_spark_yarn_executor_memory_overhead",
            "value" : "577"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_metastore_database_host",
          "value" : "ip-172-31-29-173.ec2.internal"
        }, {
          "name" : "hive_metastore_database_password",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hive-GATEWAY-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-16cb270f1651e2926b6c065435362b72",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-04257c2b71a51e68a"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-3aaabfb46ca56ec6a6f21095b9001a92",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-0828350b9c729d762"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-78d252c62ca0134a8b49cfbae4aef389",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-04d601d9726ed2629"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-GATEWAY-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "GATEWAY",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hive-HIVEMETASTORE-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "HIVEMETASTORE",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "8hd34g1jq3pem2dr6524y764v"
          } ]
        }
      }, {
        "name" : "hive-HIVESERVER2-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "HIVESERVER2",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "a69v5y0p505ph08w0rk0w27ih"
          } ]
        }
      } ],
      "displayName" : "Hive"
    }, {
      "name" : "zookeeper",
      "type" : "ZOOKEEPER",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "SERVER",
          "items" : [ {
            "name" : "zookeeper_server_java_heapsize",
            "value" : "813694976"
          } ]
        } ],
        "items" : [ ]
      },
      "roles" : [ {
        "name" : "zookeeper-SERVER-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3fp3l161vkivptt7q78b9m2ru"
          }, {
            "name" : "serverId",
            "value" : "1"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-3aaabfb46ca56ec6a6f21095b9001a92",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-0828350b9c729d762"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2ya4ghixub3cuurn5zg4bxj7l"
          }, {
            "name" : "serverId",
            "value" : "3"
          } ]
        }
      }, {
        "name" : "zookeeper-SERVER-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "SERVER",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2kxkxmku26stpm5y3swjzicyn"
          }, {
            "name" : "serverId",
            "value" : "2"
          } ]
        }
      } ],
      "displayName" : "ZooKeeper"
    }, {
      "name" : "hue",
      "type" : "HUE",
      "config" : {
        "roleTypeConfigs" : [ ],
        "items" : [ {
          "name" : "database_host",
          "value" : "ip-172-31-29-173.ec2.internal"
        }, {
          "name" : "database_password",
          "value" : "hue"
        }, {
          "name" : "database_type",
          "value" : "mysql"
        }, {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "hue_webhdfs",
          "value" : "hdfs-HTTPFS-8497ee643df2d48e3e0ef344c2dcd0c5"
        }, {
          "name" : "oozie_service",
          "value" : "oozie"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hue-HUE_SERVER-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "HUE_SERVER",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2gkj88b640puit9ukengbx1nr"
          }, {
            "name" : "secret_key",
            "value" : "oX2E8UjNLzOfam3CTJTnAAS8fKEuLh"
          } ]
        }
      } ],
      "displayName" : "Hue"
    }, {
      "name" : "oozie",
      "type" : "OOZIE",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "OOZIE_SERVER",
          "items" : [ {
            "name" : "oozie_database_host",
            "value" : "ip-172-31-29-173.ec2.internal"
          }, {
            "name" : "oozie_database_password",
            "value" : "oozie"
          }, {
            "name" : "oozie_database_type",
            "value" : "mysql"
          }, {
            "name" : "oozie_database_user",
            "value" : "oozie"
          } ]
        } ],
        "items" : [ {
          "name" : "hive_service",
          "value" : "hive"
        }, {
          "name" : "mapreduce_yarn_service",
          "value" : "yarn"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "oozie-OOZIE_SERVER-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "OOZIE_SERVER",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1tifipprpvkw08pha1m80yp4v"
          } ]
        }
      } ],
      "displayName" : "Oozie"
    }, {
      "name" : "yarn",
      "type" : "YARN",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "mapred_reduce_tasks",
            "value" : "6"
          }, {
            "name" : "mapred_submit_replication",
            "value" : "1"
          } ]
        }, {
          "roleType" : "JOBHISTORY",
          "items" : [ {
            "name" : "mr2_jobhistory_java_heapsize",
            "value" : "813694976"
          } ]
        }, {
          "roleType" : "NODEMANAGER",
          "items" : [ {
            "name" : "rm_cpu_shares",
            "value" : "1500"
          }, {
            "name" : "rm_io_weight",
            "value" : "750"
          }, {
            "name" : "yarn_nodemanager_heartbeat_interval_ms",
            "value" : "100"
          }, {
            "name" : "yarn_nodemanager_local_dirs",
            "value" : "/yarn/nm"
          }, {
            "name" : "yarn_nodemanager_log_dirs",
            "value" : "/yarn/container-logs"
          }, {
            "name" : "yarn_nodemanager_resource_cpu_vcores",
            "value" : "3"
          }, {
            "name" : "yarn_nodemanager_resource_memory_mb",
            "value" : "4939"
          } ]
        }, {
          "roleType" : "RESOURCEMANAGER",
          "items" : [ {
            "name" : "resource_manager_java_heapsize",
            "value" : "813694976"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_mb",
            "value" : "4939"
          }, {
            "name" : "yarn_scheduler_maximum_allocation_vcores",
            "value" : "3"
          } ]
        } ],
        "items" : [ {
          "name" : "hdfs_service",
          "value" : "hdfs"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "75"
        }, {
          "name" : "yarn_service_cgroups",
          "value" : "false"
        }, {
          "name" : "yarn_service_lce_always",
          "value" : "false"
        }, {
          "name" : "zk_authorization_secret_key",
          "value" : "LMQ1wRSIsGdr2VTQhjtja7SBmPZSXw"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "yarn-JOBHISTORY-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "JOBHISTORY",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9y6ztbpf0u431xq6tc6osjk5q"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-16cb270f1651e2926b6c065435362b72",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-04257c2b71a51e68a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1lyiht6m687qo2zhuq7ar39ev"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-3aaabfb46ca56ec6a6f21095b9001a92",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-0828350b9c729d762"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "hnzgirtc8bir6zksox005ni2"
          } ]
        }
      }, {
        "name" : "yarn-NODEMANAGER-78d252c62ca0134a8b49cfbae4aef389",
        "type" : "NODEMANAGER",
        "hostRef" : {
          "hostId" : "i-04d601d9726ed2629"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "2wfdw8q9sc37tf9rbu3msnkv9"
          } ]
        }
      }, {
        "name" : "yarn-RESOURCEMANAGER-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "RESOURCEMANAGER",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "rm_id",
            "value" : "50"
          }, {
            "name" : "role_jceks_password",
            "value" : "6va1f52vfxw23m8ibjxrmk9kf"
          } ]
        }
      } ],
      "displayName" : "YARN (MR2 Included)"
    }, {
      "name" : "hdfs",
      "type" : "HDFS",
      "config" : {
        "roleTypeConfigs" : [ {
          "roleType" : "BALANCER",
          "items" : [ {
            "name" : "balancer_java_heapsize",
            "value" : "813694976"
          } ]
        }, {
          "roleType" : "DATANODE",
          "items" : [ {
            "name" : "datanode_java_heapsize",
            "value" : "1073741824"
          }, {
            "name" : "dfs_data_dir_list",
            "value" : "/dfs/dn"
          }, {
            "name" : "dfs_datanode_du_reserved",
            "value" : "4293264998"
          }, {
            "name" : "dfs_datanode_max_locked_memory",
            "value" : "4294967296"
          }, {
            "name" : "rm_cpu_shares",
            "value" : "500"
          }, {
            "name" : "rm_io_weight",
            "value" : "250"
          } ]
        }, {
          "roleType" : "GATEWAY",
          "items" : [ {
            "name" : "dfs_client_use_trash",
            "value" : "true"
          } ]
        }, {
          "roleType" : "JOURNALNODE",
          "items" : [ {
            "name" : "dfs_journalnode_edits_dir",
            "value" : "/dfs/jn"
          } ]
        }, {
          "roleType" : "NAMENODE",
          "items" : [ {
            "name" : "dfs_name_dir_list",
            "value" : "/dfs/nn"
          }, {
            "name" : "dfs_namenode_servicerpc_address",
            "value" : "8022"
          } ]
        }, {
          "roleType" : "SECONDARYNAMENODE",
          "items" : [ {
            "name" : "fs_checkpoint_dir_list",
            "value" : "/dfs/snn"
          } ]
        } ],
        "items" : [ {
          "name" : "dfs_ha_fencing_cloudera_manager_secret_key",
          "value" : "V2Qif3JbHOJzc6BquoUWHtNGyeuDmf"
        }, {
          "name" : "dfs_ha_fencing_methods",
          "value" : "shell(true)"
        }, {
          "name" : "fc_authorization_secret_key",
          "value" : "ENwx8KGcgatqLnRNdtRgIMIUqLZRek"
        }, {
          "name" : "http_auth_signature_secret",
          "value" : "LDaGcywtY2v7ugwf2S6VYGGKnDAG5B"
        }, {
          "name" : "rm_dirty",
          "value" : "false"
        }, {
          "name" : "rm_last_allocation_percentage",
          "value" : "25"
        }, {
          "name" : "zookeeper_service",
          "value" : "zookeeper"
        } ]
      },
      "roles" : [ {
        "name" : "hdfs-BALANCER-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "BALANCER",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ ]
        }
      }, {
        "name" : "hdfs-DATANODE-16cb270f1651e2926b6c065435362b72",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-04257c2b71a51e68a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cq7l91rknkeyzd4a5cdgv3rhv"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-3aaabfb46ca56ec6a6f21095b9001a92",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-0828350b9c729d762"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "9sn61ozol8hwu9hx4t4tjk9ee"
          } ]
        }
      }, {
        "name" : "hdfs-DATANODE-78d252c62ca0134a8b49cfbae4aef389",
        "type" : "DATANODE",
        "hostRef" : {
          "hostId" : "i-04d601d9726ed2629"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "bc0js65ryxqr338i7pwldt4ca"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "53kvnjteroffhlk2559nv94f2"
          } ]
        }
      }, {
        "name" : "hdfs-FAILOVERCONTROLLER-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "FAILOVERCONTROLLER",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "eobhpcc7oazq0f23mv7oclppj"
          } ]
        }
      }, {
        "name" : "hdfs-HTTPFS-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "HTTPFS",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "3cv941vtdcc264w8jv6d2j7j"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "1g4mx8111fdvoo6uf0xadjvkj"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-3aaabfb46ca56ec6a6f21095b9001a92",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-0828350b9c729d762"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "cljbsrk6x0tyxef8kv0gn2wdb"
          } ]
        }
      }, {
        "name" : "hdfs-JOURNALNODE-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "JOURNALNODE",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "role_jceks_password",
            "value" : "681s7wphjd7b0zerqwvfx6kx6"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-10eeb96f4126d9cec49d5a9f92d7696a",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-0c0bead66ab53b565"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "jerry-anderson"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "jerry-anderson"
          }, {
            "name" : "namenode_id",
            "value" : "52"
          }, {
            "name" : "role_jceks_password",
            "value" : "5io28lqfgx225cm6v78moev7l"
          } ]
        }
      }, {
        "name" : "hdfs-NAMENODE-8497ee643df2d48e3e0ef344c2dcd0c5",
        "type" : "NAMENODE",
        "hostRef" : {
          "hostId" : "i-01f2cdcb6c9e8dd1a"
        },
        "config" : {
          "items" : [ {
            "name" : "autofailover_enabled",
            "value" : "true"
          }, {
            "name" : "dfs_federation_namenode_nameservice",
            "value" : "jerry-anderson"
          }, {
            "name" : "dfs_namenode_quorum_journal_name",
            "value" : "jerry-anderson"
          }, {
            "name" : "namenode_id",
            "value" : "57"
          }, {
            "name" : "role_jceks_password",
            "value" : "2299c04c57mpphdvym5w2er69"
          } ]
        }
      } ],
      "displayName" : "HDFS"
    } ]
  } ],
  "hosts" : [ {
    "hostId" : "i-0c0bead66ab53b565",
    "ipAddress" : "172.31.29.173",
    "hostname" : "ip-172-31-29-173.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-01f2cdcb6c9e8dd1a",
    "ipAddress" : "172.31.29.174",
    "hostname" : "ip-172-31-29-174.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-0828350b9c729d762",
    "ipAddress" : "172.31.29.175",
    "hostname" : "ip-172-31-29-175.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-04d601d9726ed2629",
    "ipAddress" : "172.31.29.176",
    "hostname" : "ip-172-31-29-176.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  }, {
    "hostId" : "i-04257c2b71a51e68a",
    "ipAddress" : "172.31.29.177",
    "hostname" : "ip-172-31-29-177.ec2.internal",
    "rackId" : "/default",
    "config" : {
      "items" : [ ]
    }
  } ],
  "users" : [ {
    "name" : "__cloudera_internal_user__4b7c5c14-a9ac-4cad-aa27-48fb584aa5a0",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "e3731431dd539b332f9d62fa97968cc84abb65991bae628cc9a9b1a139bd4d87",
    "pwSalt" : -8812674617911285035,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-EVENTSERVER-10eeb96f4126d9cec49d5a9f92d7696a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "20c28b5398547edc152083efc0dc996d1ae18e89d367fadf437f3832e37f020d",
    "pwSalt" : -7394243240062427714,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-HOSTMONITOR-10eeb96f4126d9cec49d5a9f92d7696a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "b2d220b31979b9bd0522ab0b87d5e24cca75d1f793868fb5271dcd389832dbc7",
    "pwSalt" : -5055764601786571902,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-REPORTSMANAGER-10eeb96f4126d9cec49d5a9f92d7696a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "993ab1c98d2c241618b7a5aa159902881380cc4143045583c18159a352058f6b",
    "pwSalt" : 8650572674339559048,
    "pwLogin" : true
  }, {
    "name" : "__cloudera_internal_user__mgmt-SERVICEMONITOR-10eeb96f4126d9cec49d5a9f92d7696a",
    "roles" : [ "ROLE_USER" ],
    "pwHash" : "7e05b14bb4b9e1ffe166463f7d5b14e71bea741f37851eea001bd498f6f7cb16",
    "pwSalt" : -3072731021999037878,
    "pwLogin" : true
  }, {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ],
    "pwHash" : "c92ce090894258c3b36c7171f9a9802d10c9f5e77778334966a34464aee8de11",
    "pwSalt" : -7625445118487032906,
    "pwLogin" : true
  }, {
    "name" : "jerry-anderson",
    "roles" : [ "ROLE_ADMIN" ],
    "pwHash" : "e68c8aecf3c5aa240c9ab93d76f2be3bdb59395aaf0803774e829493e1b742ad",
    "pwSalt" : 3389502666895905198,
    "pwLogin" : true
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ],
    "pwHash" : "14c5be4404e6a508a56a44a7f9a5b04dd444fb08bb63f826593eec3d666248c4",
    "pwSalt" : 8529169528220807873,
    "pwLogin" : true
  } ],
  "versionInfo" : {
    "version" : "5.8.1",
    "buildUser" : "jenkins",
    "buildTimestamp" : "20160722-1141",
    "gitHash" : "a0886a893750079a4dc7f902be22d6f6e63b85a1",
    "snapshot" : false
  },
  "managementService" : {
    "name" : "mgmt",
    "type" : "MGMT",
    "config" : {
      "roleTypeConfigs" : [ {
        "roleType" : "EVENTSERVER",
        "items" : [ {
          "name" : "event_server_heapsize",
          "value" : "813694976"
        } ]
      }, {
        "roleType" : "HOSTMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      }, {
        "roleType" : "REPORTSMANAGER",
        "items" : [ {
          "name" : "headlamp_database_host",
          "value" : "ip-172-31-29-173.ec2.internal"
        }, {
          "name" : "headlamp_database_name",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_password",
          "value" : "rman"
        }, {
          "name" : "headlamp_database_user",
          "value" : "rman"
        }, {
          "name" : "headlamp_heapsize",
          "value" : "813694976"
        } ]
      }, {
        "roleType" : "SERVICEMONITOR",
        "items" : [ {
          "name" : "firehose_non_java_memory_bytes",
          "value" : "1610612736"
        } ]
      } ],
      "items" : [ ]
    },
    "roles" : [ {
      "name" : "mgmt-ALERTPUBLISHER-10eeb96f4126d9cec49d5a9f92d7696a",
      "type" : "ALERTPUBLISHER",
      "hostRef" : {
        "hostId" : "i-0c0bead66ab53b565"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "10zcrswb5nme8hoqtesyuzhet"
        } ]
      }
    }, {
      "name" : "mgmt-EVENTSERVER-10eeb96f4126d9cec49d5a9f92d7696a",
      "type" : "EVENTSERVER",
      "hostRef" : {
        "hostId" : "i-0c0bead66ab53b565"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "1yu2vzwqbsdbnrcvz22ki9059"
        } ]
      }
    }, {
      "name" : "mgmt-HOSTMONITOR-10eeb96f4126d9cec49d5a9f92d7696a",
      "type" : "HOSTMONITOR",
      "hostRef" : {
        "hostId" : "i-0c0bead66ab53b565"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "an5fl0rjdurd9go9hyvb6dzix"
        } ]
      }
    }, {
      "name" : "mgmt-REPORTSMANAGER-10eeb96f4126d9cec49d5a9f92d7696a",
      "type" : "REPORTSMANAGER",
      "hostRef" : {
        "hostId" : "i-0c0bead66ab53b565"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "6uu00xnwagn2fr7kwflfqbta8"
        } ]
      }
    }, {
      "name" : "mgmt-SERVICEMONITOR-10eeb96f4126d9cec49d5a9f92d7696a",
      "type" : "SERVICEMONITOR",
      "hostRef" : {
        "hostId" : "i-0c0bead66ab53b565"
      },
      "config" : {
        "items" : [ {
          "name" : "role_jceks_password",
          "value" : "a3u686wcznbt4p44wzbg4phzm"
        } ]
      }
    } ],
    "displayName" : "Cloudera Management Service"
  },
  "managerSettings" : {
    "items" : [ {
      "name" : "CLUSTER_STATS_START",
      "value" : "10/24/2012 8:20"
    }, {
      "name" : "PUBLIC_CLOUD_STATUS",
      "value" : "ON_PUBLIC_CLOUD"
    }, {
      "name" : "REMOTE_PARCEL_REPO_URLS",
      "value" : "http://ip-172-31-29-173.ec2.internal/cdh580/,https://archive.cloudera.com/cdh5/parcels/{latest_supported}/,https://archive.cloudera.com/cdh4/parcels/latest/,https://archive.cloudera.com/impala/parcels/latest/,https://archive.cloudera.com/search/parcels/latest/,https://archive.cloudera.com/accumulo/parcels/1.4/,https://archive.cloudera.com/accumulo-c5/parcels/latest/,https://archive.cloudera.com/kafka/parcels/latest/,https://archive.cloudera.com/navigator-keytrustee5/parcels/latest/,https://archive.cloudera.com/spark/parcels/latest/,https://archive.cloudera.com/sqoop-connectors/parcels/latest/"
    } ]
  }
}
```