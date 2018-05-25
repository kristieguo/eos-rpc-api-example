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

### POST /v1/chain/get_currency_balance

##### REQUEST
```
{  
   "account":"tester",
   "code":"eosio.token",
   "symbol":"EOS"
}
```

##### RESPONSE
```
[
    "10017.6146 EOS"
]
```

### POST /v1/chain/abi_bin_to_json

##### REQUEST
```
{  
   "code":"eosio.token",
   "action":"transfer",
   "binargs":"000000005c95b1ca00000000007015d6102700000000000004454f5300000000087472616e73666572"
}
```

##### RESPONSE
```
{  
   "args":{  
      "from":"tester",
      "to":"user",
      "quantity":"1.0000 EOS",
      "memo":"transfer"
   },
   "required_scope":[  

   ],
   "required_auth":[  

   ]
}
```

### POST /v1/chain/get_table_rows

##### REQUEST
```
{  
   "scope":"tester",
   "code":"eosio.token",
   "table":"accounts",
   "json":true
}
```

##### RESPONSE
```
{
    "rows": [
        {
            "balance": "10017.6146 EOS"
        }
    ],
    "more": false
}
```

### POST /v1/history/get_actions

##### REQUEST
```
{  
   "account_name":"tester",
   "pos":1,
   "offset":1
}
```

##### RESPONSE
```
{  
   "actions":[  
      {  
         "global_action_seq":1446,
         "account_action_seq":1,
         "block_num":1427,
         "block_time":"2018-05-24T09:23:59.500",
         "action_trace":{  
            "receipt":{  
               "receiver":"tester",
               "act_digest":"563edab5729e7548f3ad704e2df5c1044eddbfe4e4a81b91d700466512ee0f37",
               "global_sequence":1446,
               "recv_sequence":2,
               "auth_sequence":[  
                  [  
                     "user",
                     3
                  ]
               ],
               "code_sequence":1,
               "abi_sequence":1
            },
            "act":{  
               "account":"eosio.token",
               "name":"transfer",
               "authorization":[  
                  {  
                     "actor":"user",
                     "permission":"active"
                  }
               ],
               "data":{  
                  "from":"user",
                  "to":"tester",
                  "quantity":"1.2340 EOS",
                  "memo":"m"
               },
               "hex_data":"00000000007015d6000000005c95b1ca343000000000000004454f5300000000016d"
            },
            "elapsed":4,
            "cpu_usage":0,
            "console":"",
            "total_cpu_usage":0,
            "trx_id":"f90bbc85b48f19d9d771a1a765fc15d2f2a166a24bbf2d257a84a977408e19c1",
            "inline_traces":[  

            ]
         }
      },
      {  
         "global_action_seq":1927,
         "account_action_seq":2,
         "block_num":1901,
         "block_time":"2018-05-24T09:27:56.500",
         "action_trace":{  
            "receipt":{  
               "receiver":"tester",
               "act_digest":"442eb822d644686d33de3741cdf0e499e437aa07c29fabb430c46c6c2f7791eb",
               "global_sequence":1927,
               "recv_sequence":3,
               "auth_sequence":[  
                  [  
                     "kris",
                     3
                  ]
               ],
               "code_sequence":1,
               "abi_sequence":1
            },
            "act":{  
               "account":"eosio.token",
               "name":"transfer",
               "authorization":[  
                  {  
                     "actor":"kris",
                     "permission":"active"
                  }
               ],
               "data":{  
                  "from":"kris",
                  "to":"tester",
                  "quantity":"1.2340 EOS",
                  "memo":"m"
               },
               "hex_data":"000000000080dd85000000005c95b1ca343000000000000004454f5300000000016d"
            },
            "elapsed":3,
            "cpu_usage":0,
            "console":"",
            "total_cpu_usage":0,
            "trx_id":"7821509b2a296d1626d0ec790e9d1e8d548a73ee86c11ef68e521429f637a3df",
            "inline_traces":[  

            ]
         }
      }
   ],
   "last_irreversible_block":115138
}
```

### POST /v1/history/get_transaction

##### REQUEST
```
{"id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1"}
```

##### RESPONSE
```
{  
   "id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1",
   "trx":{  
      "receipt":{  
         "status":"executed",
         "cpu_usage_us":732,
         "net_usage_words":28,
         "trx":[  
            1,
            {  
               "signatures":[  
                  "SIG_K1_Kco3t6gd92yxpU2qL4Gv6BAzNQJ8sk7iTRAUDUx7Tm9wzEAPH1R7ZzPZduoHeycZpgxa9oqqnsVqwhWh4qeWtkryjK5Ht8"
               ],
               "compression":"none",
               "packed_context_free_data":"",
               "packed_trx":"13f4075b0371c3a932ff000000000100a6823403ea3055000000572d3ccdcd01000000005c95b1ca00000000a8ed323229000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e7366657200"
            }
         ]
      },
      "trx":{  
         "expiration":"2018-05-25T11:31:31",
         "ref_block_num":28931,
         "ref_block_prefix":4281510339,
         "max_net_usage_words":0,
         "max_cpu_usage_ms":0,
         "delay_sec":0,
         "context_free_actions":[  

         ],
         "actions":[  
            {  
               "account":"eosio.token",
               "name":"transfer",
               "authorization":[  
                  {  
                     "actor":"tester",
                     "permission":"active"
                  }
               ],
               "data":{  
                  "from":"tester",
                  "to":"kris",
                  "quantity":"1.2222 EOS",
                  "memo":"transfer"
               },
               "hex_data":"000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e73666572"
            }
         ],
         "transaction_extensions":[  

         ],
         "signatures":[  
            "SIG_K1_Kco3t6gd92yxpU2qL4Gv6BAzNQJ8sk7iTRAUDUx7Tm9wzEAPH1R7ZzPZduoHeycZpgxa9oqqnsVqwhWh4qeWtkryjK5Ht8"
         ],
         "context_free_data":[  

         ]
      }
   },
   "block_time":"2018-05-25T11:30:32.500",
   "block_num":94472,
   "last_irreversible_block":115438,
   "traces":[  
      {  
         "receipt":{  
            "receiver":"eosio.token",
            "act_digest":"3c4745436bdcf883032f9a917ac961e740d5ebbdd8f54b3966bdbf6c679006af",
            "global_sequence":94559,
            "recv_sequence":30,
            "auth_sequence":[  
               [  
                  "tester",
                  22
               ]
            ],
            "code_sequence":1,
            "abi_sequence":1
         },
         "act":{  
            "account":"eosio.token",
            "name":"transfer",
            "authorization":[  
               {  
                  "actor":"tester",
                  "permission":"active"
               }
            ],
            "data":{  
               "from":"tester",
               "to":"kris",
               "quantity":"1.2222 EOS",
               "memo":"transfer"
            },
            "hex_data":"000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e73666572"
         },
         "elapsed":540,
         "cpu_usage":0,
         "console":"",
         "total_cpu_usage":0,
         "trx_id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1",
         "inline_traces":[  
            {  
               "receipt":{  
                  "receiver":"tester",
                  "act_digest":"3c4745436bdcf883032f9a917ac961e740d5ebbdd8f54b3966bdbf6c679006af",
                  "global_sequence":94560,
                  "recv_sequence":24,
                  "auth_sequence":[  
                     [  
                        "tester",
                        23
                     ]
                  ],
                  "code_sequence":1,
                  "abi_sequence":1
               },
               "act":{  
                  "account":"eosio.token",
                  "name":"transfer",
                  "authorization":[  
                     {  
                        "actor":"tester",
                        "permission":"active"
                     }
                  ],
                  "data":{  
                     "from":"tester",
                     "to":"kris",
                     "quantity":"1.2222 EOS",
                     "memo":"transfer"
                  },
                  "hex_data":"000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e73666572"
               },
               "elapsed":4,
               "cpu_usage":0,
               "console":"",
               "total_cpu_usage":0,
               "trx_id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1",
               "inline_traces":[  

               ]
            },
            {  
               "receipt":{  
                  "receiver":"kris",
                  "act_digest":"3c4745436bdcf883032f9a917ac961e740d5ebbdd8f54b3966bdbf6c679006af",
                  "global_sequence":94561,
                  "recv_sequence":23,
                  "auth_sequence":[  
                     [  
                        "tester",
                        24
                     ]
                  ],
                  "code_sequence":1,
                  "abi_sequence":1
               },
               "act":{  
                  "account":"eosio.token",
                  "name":"transfer",
                  "authorization":[  
                     {  
                        "actor":"tester",
                        "permission":"active"
                     }
                  ],
                  "data":{  
                     "from":"tester",
                     "to":"kris",
                     "quantity":"1.2222 EOS",
                     "memo":"transfer"
                  },
                  "hex_data":"000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e73666572"
               },
               "elapsed":4,
               "cpu_usage":0,
               "console":"",
               "total_cpu_usage":0,
               "trx_id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1",
               "inline_traces":[  

               ]
            }
         ]
      },
      {  
         "receipt":{  
            "receiver":"tester",
            "act_digest":"3c4745436bdcf883032f9a917ac961e740d5ebbdd8f54b3966bdbf6c679006af",
            "global_sequence":94560,
            "recv_sequence":24,
            "auth_sequence":[  
               [  
                  "tester",
                  23
               ]
            ],
            "code_sequence":1,
            "abi_sequence":1
         },
         "act":{  
            "account":"eosio.token",
            "name":"transfer",
            "authorization":[  
               {  
                  "actor":"tester",
                  "permission":"active"
               }
            ],
            "data":{  
               "from":"tester",
               "to":"kris",
               "quantity":"1.2222 EOS",
               "memo":"transfer"
            },
            "hex_data":"000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e73666572"
         },
         "elapsed":4,
         "cpu_usage":0,
         "console":"",
         "total_cpu_usage":0,
         "trx_id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1",
         "inline_traces":[  

         ]
      },
      {  
         "receipt":{  
            "receiver":"kris",
            "act_digest":"3c4745436bdcf883032f9a917ac961e740d5ebbdd8f54b3966bdbf6c679006af",
            "global_sequence":94561,
            "recv_sequence":23,
            "auth_sequence":[  
               [  
                  "tester",
                  24
               ]
            ],
            "code_sequence":1,
            "abi_sequence":1
         },
         "act":{  
            "account":"eosio.token",
            "name":"transfer",
            "authorization":[  
               {  
                  "actor":"tester",
                  "permission":"active"
               }
            ],
            "data":{  
               "from":"tester",
               "to":"kris",
               "quantity":"1.2222 EOS",
               "memo":"transfer"
            },
            "hex_data":"000000005c95b1ca000000000080dd85be2f00000000000004454f5300000000087472616e73666572"
         },
         "elapsed":4,
         "cpu_usage":0,
         "console":"",
         "total_cpu_usage":0,
         "trx_id":"fff5a929cb28aca17f8038c823db137ff1978c145ad9a94a74ad80f68ff8f9a1",
         "inline_traces":[  

         ]
      }
   ]
}
```
