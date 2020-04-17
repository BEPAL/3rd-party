# App间支付调用

Scheme:bepalwallet://open?params={}

#授权登录
####参数
	{
	    "protocol": "BEPAL",
	    "version": "1.0",
	    "dappName": "App名字",
	    "dappIcon": "App图标http开头",
	    "blockchain": "iost",
	    "scheme": "App的Scheme  会通过这调用你的App  规则就是scheme://open?params={}",
	    "action": "login",
	    "actionId": "自定义的原样返回"
	}

####成功
	{
	    "sign": "对 actionId 先utf-8再sha3256进行签名 和iost普通交易签名格式一致",
	    "wallet": "账户名字",
	    "ref": "BEPAL",
	    "action": "login",
	    "authorize": "BEPAL自定义的一个参数无需解析 后面所有转账操作都需要带这个参数",
	    "actionId": "自定义的原样返回",
	    "publickey": "账户公钥",
	    "permissions": [
	        "active",
	        "owner"
	    ],
	    "result": 1
	}

####失败
	{
	    "action": "login",
	    "actionId": "自定义的原样返回",
	    "result": 0
	}

#转账
####参数
	{
	    "protocol": "BEPAL",
	    "version": "1.0",
	    "dappName": "App名字",
	    "dappIcon": "App图标http开头",
	    "blockchain": "iost",
	    "scheme": "App的Scheme  会通过这调用你的App  规则就是scheme://open?params={}",
	    "action": "transfer",
	    "authorize": "BEPAL自定义的一个参数无需解析 后面所有转账操作都需要带这个参数",
	    "actionId": "自定义的原样返回",
	    "contract": "token.iost",
	    "action_name": "transfer",//要判断是否等于transfer 不是交易不给执行
	    "data": [ //普通交易的那些参数
	        "iost",
	        "from",
	        "to",
	        "amount",
	        "memo"
	    ]
	}
####成功
	{
	    "ref": "BEPAL",
	    "txID": "交易id",
	    "action": "transfer",
	    "actionId": "自定义的原样返回",
	    "wallet": "账户名",
	    "result": 1
	}
####失败
	{
	    "action": "transfer",
	    "actionId": "自定义的原样返回",
	    "result": 0
	}

####消息签名
####参数
	{
	    "protocol": "BEPAL",
	    "version": "1.0",
	    "dappName": "App名字",
	    "dappIcon": "App图标http开头",
	    "blockchain": "iost",
	    "scheme": "App的Scheme  会通过这调用你的App  规则就是scheme://open?params={}",
	    "action": "sign",
	    "authorize": "BEPAL自定义的一个参数无需解析 后面所有转账操作都需要带这个参数",
	    "actionId": "自定义的原样返回",
	    "message": "签名内容 先utf-8再sha3256进行签名 和iost普通交易签名格式一致"
	}
####成功
	{
	    "ref": "BEPAL",
	    "sign": "是对签名内容先utf-8再sha3256进行签名的结果 和iost普通交易签名格式一致",
	    "action": "sign",
	    "actionId": "自定义的原样返回",
	    "wallet": "账户名",
	    "result": 1
	}
####失败
	{
	    "action": "sign",
	    "actionId": "自定义的原样返回",
	    "result": 0
	}
####BEPAL打开DApp
####参数
	{
	    "protocol": "BEPAL",
	    "version": "1.0",
	    "action": "opendapp",
	    "url": "http开头"
	}

