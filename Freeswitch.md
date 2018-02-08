#### getting users
```
show registrations
```

#### creating a call from free switch
```
originate {origination_caller_id_name='Xeon Zolt',origination_caller_id_number=123456789}sofia/internal/sip:1001@10.60.18.33:35722 &park()
```
<details>
originate --> command

{ } --> to set caller info 

 |___ origination_caller_id_name --> set caller name
 
 |___ origination_caller_id_number --> set caller id number
 
 sofia/internal --> channel
 sip:1001@10.60.18.33:35722 --> address
</details>

#### bridging a call a call from free switch
```
originate sofia/internal/sip:1001@10.60.18.33:35722 &bridge(sofia/internal/sip:1002@10.60.18.40:63559)
```

