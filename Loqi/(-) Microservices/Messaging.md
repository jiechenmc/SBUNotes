#loqi #service

```

The following operations can be performed through the API

Create
Update
Delete

calls can be made to: /api/messaging

```

<h1><font style="color:lightblue">GET (Reserved For Testing)</font></h1>

***Request Body***

```json
{
	fullMessagePath: string
}
```

***Response Body***

<font style="color:lightgreen">200 (OK)</font>
```json
{
    "author": string,
    "content": string,
    "timeCreated": number
}
```
<font style="color:red">404 (Not Found)</font>
```json
{}
```

<h1><font style="color:lightblue">POST</font></h1>

***Request Body***

```json
{
	collectionPath: string,
	Content: string,
}
```

***Response Body***

<font style="color:lightgreen">200 (OK)</font>
```json
{
    "messageID": string,
}
```
<font style="color:red">ERR (TBD)</font>
```json
{}
```

<h1><font style="color:lightblue">PATCH</font></h1>
***Request Body**

```json
{
	TBD
}
```

***Response Body***

<font style="color:lightgreen">200 (OK)</font>
```json
{
    TBD
}
```
<font style="color:red">ERR (TBD)</font>
```json
TBD
```

<h1><font style="color:lightblue">DELETE</font></h1>
***Request Body***

```json
{
	fullMessagePath: string
}
```

***Response Body***

<font style="color:lightgreen">200 (OK)</font>
```json
{
    removed: string
}
```
<font style="color:red">404 (Not Found)</font>
```json
{}
```

