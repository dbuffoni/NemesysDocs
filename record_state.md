```
@startuml
Title Scoring record state chart
[*] --> Outstanding: USR:Calculate
Outstanding --> Submitted : USR:Submit
Outstanding --> Outstanding : USR:Recalculate
Submitted  --> Approved: MAN:Approve
Submitted  --> Outstanding: MAN:Reject
Approved --> Validating: USR:Validate
Approved --> Outstanding: MAN:Invalidate
Validating --> Validated: DLT:Validation
Validated --> [*] : SYS:Archive
note left of Outstanding : Track record for each state\n change to table score_track
note left of Validated :  Archive to table score_history\nInForce to table score_inforce


state Validated {
[*] --> Valid 
[*] --> NotValid
Valid --> [*] : SYS:InForce
NotValid --> [*]
}
@enduml
```
