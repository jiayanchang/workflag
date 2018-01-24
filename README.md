# workflag

请求统一前缀：yanchang.info/strawberry

## 列表接口

1. url: /projects
1. method: post
1. content-type:application/json

request perematers

```json

{
	status:'processing',  //value is all or processing
	sorts :['level', 'status']
}

```

response data:

```json
{
	code:200,
	msg:'',
	data:[
		{
			'id':	1,
			'name':	'a project',
			'status': 'waitting',  	//waitting\developing\testing\completed\archived
			'level':	1
		}
	]
}

```

## 项目数据

1. url: /project/{id}
2. method: GET

request perematers

response data:

```json
{
	code:200,
	msg:'',
	data:[
		{
			'id':	1,
			'name':	'a project',
			'model':	'basic',
			'status': 'waitting',  	//waitting\developing\testing\completed\archived
			'level':	1,
			'pm': 'james',
			'team_leader':'wade',
			'developers':{
				'h5': ['wade','james','kobe'],
				'java': ['garnnet'],
				'testor': ['thomas']
			},
			'def_day':'2017-12-21',
			'start_day':'2017-12-21',
			'test_day':'2017-12-21',
			'complete_day':'2017-12-21',
			'note':'this is a different project',
			logs:[
				{
					log_id:12,
					'created_at': '2017-12-21 12:33:11',
					'creator':'kobe'
					'content':'normal'
				},
				{
					log_id:13,
					'created_at': '2017-12-21 12:33:11',
					'creator':'kobe'
					'content':'completed!'
				}
			]
		}
	]
}

```

## 创建/修改项目

1. url: /project/save
2. method: POST
3. content-type:application/json


request perematers

```json
{
	code:200,
	msg:'',
	data:[
		{
			'id':1, //传值表示修改，无值表示创建
			'name':	'a project',
			'model':	'basic',
			'status': 'waitting',  	//waitting\developing\testing\completed\archived
			'level':	1,
			'pm': 'james',
			'team_leader':'wade',
			'developers':{
				'h5': ['wade','james','kobe'],
				'java': ['garnnet'],
				'testor': ['thomas']
			},
			'def_day':'2017-12-21',
			'start_day':'2017-12-21',
			'test_day':'2017-12-21',
			'complete_day':'2017-12-21',
			'note':'this is a different project',
			logs:{
					'content':'normal'
				}
		}
	]
}

```

response data

```json
{
	code:200,
	msg:''
	data:{
		id:2
	}
}

```



## 添加日志

1. url: /project/log/add
2. method: POST
3. content-type:application/json


request perematers

```json

{
	projectId:1,
	'content':'completed!'
}

```

response data

```json
{
	code:200,
	msg:'',
	data:{
		'log_id':12,
		'created_at': '2017-12-21 12:33:11',
		'creator':'kobe'
	}
}

```


## 删除日志

1. url: /project/log/del
2. method: POST
3. content-type:application/json


request perematers

```json

{
	log_id:12
}

```

response data

```json
{
	code:200,
	msg:''
}

```

## 获取模块

1. url: /models
2. method: GET


response data

```json
{
	code:200,
	msg:'',
	data:[
		'basic', 'technology', 'money'
	]
}

```


## 获取开发资源

1. url: /developers
2. method: GET


response data

```json
{
	code:200,
	msg:'',
	data:{
		'h5': ['wade','james','kobe'],
		'java': ['garnnet'],
		'testor': ['thomas']
	}
}

```



## 开发资源统计

1. url: /developer/stat
2. method: GET


response data

```json
{
	code:200,
	msg:'',
	data:{
		'h5': [
			{
				'name':'wade',
				'projects':[
					{
						'id':12,
						'name':'a project'
					}
				]
			},

			{
				'name':'james',
				'projects':[
					{
						'id':13,
						'name':'b project'
					}
				]
			}
		]
		'testor': [
			{
				'name':'wade',
				'projects':[
					{
						'id':12,
						'name':'a project'
					}
				]
			},

			{
				'name':'james',
				'projects':[]
			}
		]
	}
}

```

