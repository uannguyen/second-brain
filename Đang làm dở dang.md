```json
=== req body Xu
{"orders":[{"price":1,"quantity":1,"reference":"0909090044","gift_code":"VQMMEXU68","layout_id":"VQMM"}],"discount_amount":0,"trans_amount":0,"service_type":43,"gift_code":"VQMMEXU68","transid_ref":"VQMM_1710929477342","order_id":"VQMM_1710929477342","agent_type":"MERCHANT"}
```

# Schema game

```json
{
    "_id" : ObjectId("65d84bf10a46bbe8e5d00437"),
    "channel" : "MERCHANT",
    "name" : "Vòng Quay May Mắn - Phase 2",
    "layout_id" : "VQMM",
    "banner_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1704677360886_BANNERNXUNSANGRCLCVNG2png.png",
    "spin_banner_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1704181046407_VngxoayVngquay1png.png",
    "start" : 1708621200000.0,
    "end" : 1735578000000.0,
    "accept_conditions" : {
        "condition_type" : "AND",
        "conditions" : [ 
            {
                "fact" : "reference",
                "operator" : "notIn",
                "value" : [ 
                    "0919000002"
                ]
            }, 
            {
                "fact" : "location_group_code",
                "operator" : "in",
                "value" : [ 
                    "NO", 
                    "CT", 
                    "SEN"
                ]
            }
        ]
    },
    "rules" : [ 
        {
            "key" : "DAILY_LOGIN",
            "name" : "Điểm danh mỗi ngày",
            "value" : "\"null\"",
            "index" : 1,
            "spin_rule_config" : {
                "spin_number_receive" : 1,
                "max_task_count" : {
                    "daily" : 1
                }
            },
            "gifts" : [],
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833933636_imdanhpng.png"
        }, 
        {
            "key" : "SHARE_GAME",
            "name" : "Chia sẻ lời chúc \nnăm mới",
            "value" : "\"null\"",
            "index" : 2,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : {
                    "daily" : 1
                }
            },
            "gifts" : [],
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967556932_icon2png.png",
            "content" : "#VQMM_ECODiemBan_Tet2024",
            "url" : "#VQMM_ECODiemBan_Tet2024"
        }, 
        {
            "key" : "IDENTITY",
            "name" : "Hoàn thành định danh người dùng",
            "value" : "{\"ewallet_state\":\"VERIFIED\"}",
            "index" : 3,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : null
            },
            "gifts" : [],
            "accept_conditions" : {
                "condition_type" : "AND",
                "conditions" : [ 
                    {
                        "fact" : "ewallet_state",
                        "operator" : "equal",
                        "value" : "NEW"
                    }
                ]
            },
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833987628_nhdanhpng.png"
        }, 
        {
            "key" : "BANK_LINK",
            "name" : "Liên kết tài khoản \nngân hàng",
            "value" : "{\"bankmaps\":{\"$ne\":[],\"$exists\":true}}",
            "index" : 4,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : null
            },
            "gifts" : [],
            "accept_conditions" : {
                "condition_type" : "AND",
                "conditions" : [ 
                    {
                        "fact" : "bankmaps",
                        "operator" : "doesNotContain",
                        "value" : null
                    }
                ]
            },
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png"
        }, 
        {
            "key" : "ECOM_ORDER",
            "name" : "Thanh toán mua hàng",
            "value" : "{\"status\":{\"fact\":\"status\",\"operator\":\"equal\",\"value\":\"RECEIVED\"},\"order_amount\":{\"fact\":\"order_amount\",\"operator\":\"greaterThanInclusive\",\"value\":50000}}",
            "index" : 5,
            "params" : {
                "showcase_id" : 1351601
            },
            "spin_rule_config" : {
                "spin_number_receive" : 3,
                "max_task_count" : {
                    "daily" : 1
                }
            },
            "gifts" : [],
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png"
        }, 
        {
            "key" : "ECOM_ORDER",
            "name" : "Thanh toán mua hàng",
            "value" : "{\"status\":{\"fact\":\"status\",\"operator\":\"equal\",\"value\":\"RECEIVED\"},\"order_amount\":{\"fact\":\"order_amount\",\"operator\":\"greaterThanInclusive\",\"value\":50000},\"sku\":{\"fact\":\"sku\",\"operator\":\"in\",\"value\":[\"SKUP116596V331597\"]},\"org_id\":{\"fact\":\"org_id\",\"operator\":\"in\",\"value\":[578514]}}",
            "index" : 6,
            "spin_rule_config" : {
                "spin_number_receive" : 3,
                "max_task_count" : {
                    "daily" : 1
                }
            },
            "gifts" : [],
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png"
        }, 
        {
            "key" : "TRANSACTION",
            "name" : "Thanh toán dịch vụ",
            "value" : "{\"result\":0,\"state\":2,\"transtype\":{\"$in\":[\"BUY\",\"POSTPAID\",\"BUYCODE\"]},\"amount\":{\"$gte\":10000}}",
            "index" : 7,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : {
                    "daily" : 3
                }
            },
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png",
            "gifts" : []
        }, 
        {
            "key" : "TRANSACTION",
            "name" : "Thanh toán hóa đơn",
            "value" : "{\"result\":0,\"state\":2,\"transtype\":{\"$in\":[\"BILLPAY\"]},\"amount\":{\"$gte\":300000}}",
            "index" : 8,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : {
                    "daily" : 3
                }
            },
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png",
            "gifts" : []
        }, 
        {
            "key" : "ECOM_CART",
            "name" : "Thêm sản phẩm vào giỏ hàng",
            "index" : 9,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : {
                    "daily" : 1
                }
            },
            "gifts" : [],
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png"
        }, 
        {
            "key" : "QR_PAYMENT",
            "name" : "Quét mã QR thanh toán",
            "value" : "{\"result\":0,\"state\":2,\"amount\":{\"$gte\":5000}}",
            "index" : 10,
            "spin_rule_config" : {
                "spin_number_receive" : 2,
                "max_task_count" : {
                    "daily" : 1
                }
            },
            "gifts" : [],
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833763730_Linktbankpng.png"
        }
    ],
    "status" : 1,
    "gifts" : [ 
        {
            "gift_code" : "VQMMEXU50",
            "gift_index" : 1,
            "gift_type" : "coin",
            "gift_amount" : 50,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967682899_icon7png.png"
        }, 
        {
            "gift_code" : "VQMMVC20K",
            "gift_index" : 2,
            "gift_type" : "voucher",
            "gift_amount" : 20000,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967597059_icon4png.png"
        }, 
        {
            "gift_code" : "VQMMEXU500",
            "gift_index" : 3,
            "gift_type" : "coin",
            "gift_amount" : 500,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967682899_icon7png.png"
        }, 
        {
            "gift_code" : "VQMMVC30K",
            "gift_index" : 4,
            "gift_type" : "voucher",
            "gift_amount" : 30000,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967597059_icon4png.png"
        }, 
        {
            "gift_code" : "VQMMEXU1000",
            "gift_index" : 5,
            "gift_type" : "coin",
            "gift_amount" : 1000,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967682899_icon7png.png"
        }, 
        {
            "gift_code" : "VQMMVC50K",
            "gift_index" : 6,
            "gift_type" : "voucher",
            "gift_amount" : 50000,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967597059_icon4png.png"
        }, 
        {
            "gift_code" : "VQMMCB20K",
            "gift_index" : 7,
            "gift_type" : "cashback",
            "gift_amount" : 20000,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1702967639798_icon6png.png"
        }, 
        {
            "gift_code" : "VQMMVIPSJC999",
            "gift_index" : 8,
            "gift_type" : "gift_cashback",
            "gift_amount" : 7400000,
            "icon_url" : "https://ecom-cms-test-portal.finviet.com.vn:6868/download?f=1703833850181_Tngvngpng.png"
        }
    ],
    "setting" : {
        "display" : true,
        "auto_claim" : false,
        "spin_setting" : {
            "spin_gift_configs" : [ 
                {
                    "user_type" : 0,
                    "location_group_code" : "NO",
                    "data" : [ 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMEXU50",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMEXU500",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMEXU1000",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMVC20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMVC30K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMVC50K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 3,
                            "gift_code" : "VQMMCB20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1,
                            "gift_code" : "VQMMVIPSJC999",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }
                    ]
                }, 
                {
                    "user_type" : 0,
                    "location_group_code" : "CT ",
                    "data" : [ 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMEXU50",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMEXU500",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMEXU1000",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 20,
                            "gift_code" : "VQMMVC20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 20,
                            "gift_code" : "VQMMVC30K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 20,
                            "gift_code" : "VQMMVC50K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 20,
                            "gift_code" : "VQMMCB20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1,
                            "gift_code" : "VQMMVIPSJC999",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }
                    ]
                }, 
                {
                    "user_type" : 0,
                    "location_group_code" : "SEN",
                    "data" : [ 
                        {
                            "max_gift_quantity" : 1000,
                            "gift_code" : "VQMMEXU50",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1000,
                            "gift_code" : "VQMMEXU500",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1000,
                            "gift_code" : "VQMMEXU1000",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 100,
                            "gift_code" : "VQMMVC20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 100,
                            "gift_code" : "VQMMVC30K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 100,
                            "gift_code" : "VQMMVC50K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1,
                            "gift_code" : "VQMMCB20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1,
                            "gift_code" : "VQMMVIPSJC999",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }
                    ]
                }, 
                {
                    "user_type" : 0,
                    "data" : [ 
                        {
                            "max_gift_quantity" : 1000,
                            "gift_code" : "VQMMEXU50",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1000,
                            "gift_code" : "VQMMEXU500",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1000,
                            "gift_code" : "VQMMEXU1000",
                            "rate" : 12.5,
                            "max_gift_per_user" : -1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMVC20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMVC30K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMVC50K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 200,
                            "gift_code" : "VQMMCB20K",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }, 
                        {
                            "max_gift_quantity" : 1,
                            "gift_code" : "VQMMVIPSJC999",
                            "rate" : 12.5,
                            "max_gift_per_user" : 1,
                            "accepted_phones" : []
                        }
                    ]
                }
            ],
            "spin_redeem_config" : {
                "max_spin_per_day" : 3,
                "exchange_coin" : 500
            }
        }
    },
    "info" : [ 
        {
            "title" : "Thể lệ chương trình",
            "content" : "<p>1. C&aacute;c phần qu&agrave; Điểm b&aacute;n nhận được sẽ ngẫu nhi&ecirc;n bao gồm: Tặng EXu, Voucher ho&agrave;n tiền khi mua h&agrave;ng FMCG, Tặng tiền v&agrave;o v&iacute;, Một chỉ v&agrave;ng SJC 9999</p> <ul> <li>Tặng EXu: EXu sẽ được tặng trực tiếp v&agrave;o kho EXu của Điểm b&aacute;n trong v&ograve;ng 24h kể từ khi tr&uacute;ng.</li> <li>Voucher ho&agrave;n tiền: Voucher sẽ được cộng th&ecirc;m v&agrave;o Kho qu&agrave; mục &ldquo;Qu&agrave; của t&ocirc;i&rdquo; của Điểm b&aacute;n trong v&ograve;ng 24h kể từ khi tr&uacute;ng. Ngo&agrave;i ra cũng sẽ lưu trữ trong mục &ldquo;Lịch sử&rdquo; b&ecirc;n g&oacute;c tr&aacute;i v&ograve;ng quay.</li> <li>Mỗi gi&aacute; trị voucher được ph&aacute;t tr&ecirc;n chương tr&igrave;nh, Điểm b&aacute;n tr&uacute;ng thưởng chỉ c&oacute; thể sử dụng 1 lần. Voucher ho&agrave;n tiền được ph&aacute;t c&oacute; giới hạn lượt d&ugrave;ng, lượt d&ugrave;ng c&oacute; thể hết sớm khi đạt mức giới hạn. Tất cả c&aacute;c voucher sẽ đều c&oacute; gi&aacute; trị sử dụng m&atilde; qu&agrave; tặng đến hết ng&agrave;y 20/02/2024.</li> <li>Tặng tiền v&agrave;o v&iacute;: Tiền sẽ được gửi v&agrave;o v&iacute; của Điểm b&aacute;n trong v&ograve;ng 3 ng&agrave;y kể từ khi tr&uacute;ng. Sau khi tiền được chuyển v&agrave;o v&iacute;, hệ thống sẽ gửi th&ocirc;ng b&aacute;o qua ứng dụng ECO Điếm B&aacute;n, người tr&uacute;ng giải sẽ tự động kiểm tra v&iacute; khi c&oacute; th&ocirc;ng b&aacute;o.</li> <li>Giải &ldquo;1 chỉ v&agrave;ng SJC 9999&rdquo;: Giải thưởng sẽ được lưu trữ trong mục &ldquo;Lịch sử&rdquo; (b&ecirc;n g&oacute;c tr&aacute;i v&ograve;ng quay) cho đến khi qu&agrave; đến tay Điểm B&aacute;n. ECO Điểm B&aacute;n sẽ li&ecirc;n hệ trực tiếp với Điểm b&aacute;n trong v&ograve;ng 5 ng&agrave;y l&agrave;m việc để thực hiện thủ tục nhận thưởng</li> </ul> <p>2.&nbsp; Mọi phần qu&agrave; đều c&oacute; giới hạn, chương tr&igrave;nh c&oacute; thể kết th&uacute;c sớm khi qu&agrave; đạt mức giới hạn m&agrave; kh&ocirc;ng cần b&aacute;o trước.</p> <p>3.&nbsp;ECO Điểm B&aacute;n c&oacute; quyền thay đổi c&aacute;c điều khoản cũng như ngưng chương tr&igrave;nh m&agrave; kh&ocirc;ng cần th&ocirc;ng b&aacute;o trước hoặc chịu tr&aacute;ch nhiệm với bất k&igrave; b&ecirc;n n&agrave;o.</p> <p>4.&nbsp;Khi ph&aacute;t hiện c&oacute; dấu hiệu gian lận, ECO Điểm B&aacute;n c&oacute; quyền thu hồi phần thưởng m&agrave; kh&ocirc;ng cần th&ocirc;ng b&aacute;o trước đến người chơi.</p> <p>5.&nbsp;Bằng việc tham gia chương tr&igrave;nh, anh chị đ&atilde; đọc, hiểu v&agrave; đồng &yacute; với to&agrave;n bộ thể lệ, điều khoản v&agrave; điều kiện cũng như ch&iacute;nh s&aacute;ch của chương tr&igrave;nh V&ograve;ng quay may mắn. Đồng thời, ECO Điểm B&aacute;n sẽ được ph&eacute;p c&ocirc;ng bố th&ocirc;ng tin người nhận qu&agrave; tr&ecirc;n Fanpage.<br /> &nbsp;</p>",
            "url" : "https://finviet.com.vn/vong-quay-may-man-don-xuan-sang-ruoc-vang-9999/"
        }
    ],
    "createdAt" : ISODate("2023-10-24T07:33:36.990Z"),
    "updatedAt" : ISODate("2023-10-24T07:33:36.990Z"),
    "__v" : 0
}
```