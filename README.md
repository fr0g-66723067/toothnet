# toothnet

research into the feasbility of an IoT Toothbrush botnet

## hardware and firmware
https://github.com/lozaning/Teeth @lozaning

## nvs_dump json
multiple base64 encoded values with an entry_state of "Erased" that contain key information

```
      {                                                          
        "entry_state": "Erased",                                                                                                                                                                                                                                                                                 
        "entry_ns_index": 3,                                     
        "entry_ns": "bt_config.conf",                                                                                                                   
        "entry_type": "BLOB_DATA",                                          
        "entry_span": 8,                                                                                                                                                                                                                                                                                         
        "entry_chunk_index": 0,                                                                                                                                                                                                                                                                                  
        "entry_key": "bt_cfg_key0",                                                                                                                     
        "entry_data_type": "BLOB_DATA",                         
        "entry_data_size": 216,                                        
        "entry_data": "W0FkYXB0ZXJdCkxFX0xPQ0FMX0tFWV9JUksgPSAzZWU1M2Q5MzE5N2M4MjhjOGEyOWU1YjI1YjM0N2Y0YwpMRV9MT0NBTF9LRVlfSVIgPSAyNjE2OTQwOWZkZTA4NWZkOWYwN2ZmZTRmYjliY2E5MgpMRV9MT0NBTF9LRVlfREhLID0gNjU1NTk2ZjJlM2Y3YjgyZTE0YmNhNjZjMzdiOTViYmYKTEVfTE9DQUxfS0VZX0VSID0gNDQ3ZmFhM2ZlY2NkZTQ2ZTk2NzAxMTY5YzMxNT
FlNGYK"                                                                                                                                                 
      },
```

decodes to 

```
[Adapter]
LE_LOCAL_KEY_IRK = 3ee53d93197c828c8a29e5b25b347f4c
LE_LOCAL_KEY_IR = 26169409fde085fd9f07ffe4fb9bca92
LE_LOCAL_KEY_DHk = 655596f2e3f7b82e14bca66c37b95bbf
LE_LOCAL_KEY_ER = 447faa3feccd e46e96701169c3151e4f
```
This text appears to be a configuration block, possibly for a Bluetooth Low Energy (BLE) device or software stack. The keys mentioned are likely used for security purposes in BLE communication:

    LE_LOCAL_KEY_IRK (Identity Resolving Key): Used to resolve or generate random private addresses, aiding in privacy and security.
    LE_LOCAL_KEY_IR (Identity Root): May be used to generate the IRK and other keys.
    LE_LOCAL_KEY_DHk (Device Hash Key): Likely a typo in the original text ("DHk" should be "DHK"), this key is used in generating cryptographic hashes for certain security functions.
    LE_LOCAL_KEY_ER (Encryption Root): Used to generate the Long Term Key (LTK) for encrypting the BLE link.

These keys are essential for the secure operation of BLE devices, enabling encrypted communication and protecting against eavesdropping and data tampering.

### default ssid creds for manufacturer SSID
```
      {                                                                                                                                                                                                                                                                                                          
        "entry_state": "Erased",                                                                                                                                                                                                                                                                                 
        "entry_ns_index": 5,                                                                                                                                                                                                                                                                                     
        "entry_type": "BLOB_DATA",                                                                                                                                                                                                                                                                               
        "entry_span": 3,                                                                                                                                                                                                                                                                                         
        "entry_chunk_index": 0,                                                                                                                                                                                                                                                                                  
        "entry_key": "sta.ssid",                                                                                                                                                                                                                                                                                 
        "entry_data_type": "BLOB_DATA",                                                                                                                                                                                                                                                                          
        "entry_data_size": 36,                                                                                                                                                                                                                                                                                   
        "entry_data": "CwAAAE1hbnVmYWN0dXJlAAAAAAAAAAAAAAAAAAAAAAAAAAAA"                                                                                                                                                                                                                                         
      },                                                                                                                                                                                                                                                                                                                                                                                                                                                         
      {                                                                                                                                                                                                                                                                                                          
        "entry_state": "Erased",                                                                                                                                                                                                                                                                                 
        "entry_ns_index": 5,                                                                                                                                                                                                                                                                                     
        "entry_type": "BLOB_DATA",                                                                                                                                                                                                                                                                               
        "entry_span": 4,                                                                                                                                                                                                                                                                                         
        "entry_chunk_index": 0,                                                                                                                                                                                                                                                                                  
        "entry_key": "sta.pswd",                                                                                                                                                                                                                                                                                 
        "entry_data_type": "BLOB_DATA",                                                                                                                                                                                                                                                                          
        "entry_data_size": 65,                                                                                                                                                                                                                                                                                   
        "entry_data": "ZGdldm93ZXJhAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA="                                                                                                                                                                                                 
      },
```

decodes to ```\x0b\x00\x00\x00Manufacture\x00``` and ```dgevowera```. another wireless password found ```12345678```

network hosts:
* httx://ipaddr.market.alicloudapi.com/ip_addr_search/v1?IP_ADDR=0.0.0.0
* htt://zh-api.evowera.com:8099
* mqtt://zh-emq.evowera.com


