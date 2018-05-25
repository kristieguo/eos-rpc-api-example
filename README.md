# eos-rpc-api-example

### 1. GET /v1/chain/get_info

##### RESPONSE
```
{
    "server_version": "cd979827",
    "head_block_num": 110572,
    "last_irreversible_block_num": 110571,
    "last_irreversible_block_id": "0001afeb67d2503b93e64f2e34631691989bad886dcc85777995df4aece774fc",
    "head_block_id": "0001afec64eec39550853d2e032633b1c4f987ad22f343e76cafbf8f9e6e36b4",
    "head_block_time": "2018-05-25T13:44:42",
    "head_block_producer": "eosio",
    "virtual_block_cpu_limit": "104857600000",
    "virtual_block_net_limit": 1048576000,
    "block_cpu_limit": 104857500,
    "block_net_limit": 1048576
}
```

### 1. POST /v1/chain/abi_json_to_bin 

##### REQUEST
```
{  
   "code":"eosio.token",
   "action":"transfer",
   "authorization":[  
      {  
         "actor":"tester",
         "permission":"active"
      }
   ],
   "args":{  
      "from":"tester",
      "to":"user",
      "quantity":"1.0000 EOS",
      "memo":"transfer"
   }
}
```

##### RESPONSE
```
{
    "binargs": "000000005c95b1ca00000000007015d6102700000000000004454f5300000000087472616e73666572"
}
```

### 1. POST /v1/chain/get_block

##### REQUEST
```
{"block_num_or_id":100}
```

##### RESPONSE
```
{  
   "timestamp":"2018-05-24T09:12:56.000",
   "producer":"eosio",
   "confirmed":0,
   "previous":"0000006328fadd5333bfb80ecd21646448d3858b40c0816b01b986318455943f",
   "transaction_mroot":"0000000000000000000000000000000000000000000000000000000000000000",
   "action_mroot":"4a60d816edd825751b3e364fe56e6d578f9f30852c00546117167eb5f954d540",
   "schedule_version":0,
   "new_producers":null,
   "header_extensions":[  

   ],
   "producer_signature":"SIG_K1_KiC8vBhqSArKqMS82RByKsepYagHEoa4wAi6AdMSntCaFqhZhg96Q3FCfgp9AGVhqCxnzi1LA4tA4KXrEPZx9ToWEpAZW9",
   "transactions":[  

   ],
   "block_extensions":[  

   ],
   "id":"00000064c400d036822f7d2e2fee71c47b645a07fbcb6c0491cd69d3d25dc4f8",
   "block_num":100,
   "ref_block_prefix":779956098
}
```

### POST /v1/chain/get_account

##### REQUEST
```
{"account_name":tester}
```

##### RESPONSE
```
{  
   "account_name":"tester",
   "privileged":false,
   "last_code_update":"1970-01-01T00:00:00.000",
   "created":"2018-05-24T09:14:09.000",
   "ram_quota":-1,
   "net_weight":-1,
   "cpu_weight":-1,
   "net_limit":{  
      "used":-1,
      "available":-1,
      "max":-1
   },
   "cpu_limit":{  
      "used":-1,
      "available":-1,
      "max":-1
   },
   "ram_usage":2852,
   "permissions":[  
      {  
         "perm_name":"active",
         "parent":"owner",
         "required_auth":{  
            "threshold":1,
            "keys":[  
               {  
                  "key":"EOS5T6V7jXaxweNW5eEA8EmHx6dBVEhrKesPRQWxKdqCazmphJJNK",
                  "weight":1
               }
            ],
            "accounts":[  

            ],
            "waits":[  

            ]
         }
      },
      {  
         "perm_name":"owner",
         "parent":"",
         "required_auth":{  
            "threshold":1,
            "keys":[  
               {  
                  "key":"EOS5T6V7jXaxweNW5eEA8EmHx6dBVEhrKesPRQWxKdqCazmphJJNK",
                  "weight":1
               }
            ],
            "accounts":[  

            ],
            "waits":[  

            ]
         }
      }
   ],
   "total_resources":null,
   "delegated_bandwidth":null,
   "voter_info":null
}
```

