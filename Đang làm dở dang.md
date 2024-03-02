
- Làm tới khúc update trans chỗ ApplyPromotion
- Revert promotion manual

```json
============= REQ failed

{
  "module": "agentnetwork",
  "page": "trans-details",
  "action": "updateState",
  "params": {
    "reqid": "1709178061960",
    "trans": {
      "servicetype": 6,
      "clientid": "0944985464",
      "transid": 68265749,
      "transtype": "BUY",
      "date": 1709178069242,
      "state": 6,
      "amount": 40000,
      "data": "",
      "special_agent": "vnp.airtime",
      "recipient": "0944985464",
      "result": 103,
      "result_ref": 103,
      "avail_balance": 2002000,
      "message": "Giao dịch thất bại",
      "loyalty_hold_point": {}
    }
  }
}


================= REQ success

{
  "module": "agentnetwork",
  "page": "trans-details",
  "action": "updateState",
  "params": {
    "reqid": "1709188652896",
    "trans": {
      "servicetype": 6,
      "clientid": "0944985464",
      "transid": 68265913,
      "transtype": "BUY",
      "date": 1709188659894,
      "state": 2,
      "amount": 40000,
      "data": "",
      "special_agent": "vnp.airtime",
      "recipient": "0944985464",
      "result": 0,
      "result_ref": 0,
      "avail_balance": 1962800,
      "message": "Thành công",
      "loyalty_hold_point": {}
    }
  }
}
```