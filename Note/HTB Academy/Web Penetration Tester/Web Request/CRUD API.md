- web application utilize APIs to perform search like in previous section 
- we can directly interact with API endpoint

### Application Programming Interface (API)
- among several types of APIs many are used to interact with database
- so that we are able to specify the requested table and the requested row within our API query then use and HTTP method to perform operation needed
>[!Example] 
> for the `api.php` endpoint in our example, if we wanted to update the `city` table in the database, and the row we will be updating has a city name of `london`
> `curl -X PUT http://<SERVER_IP>:<PORT>/api.php/city/london `

### CRUD
- we can easily specify the table and the row we want to perform an operation on through APIs
- we may utilize different HTTP method to perform different operations on that row 
- there are 4 main operation on the requested database entity

| Operation | HTTP Method | Description                                        |
| --------- | ----------- | -------------------------------------------------- |
| `Create`  | `POST`      | Adds the specified data to the database table      |
| `Read`    | `GET`       | Reads the specified entity from the database table |
| `Update`  | `PUT`       | Updates the data of the specified database table   |
| `Delete`  | `DELETE`    | Removes the specified row from the database table  |
- four operations are mainly linked to the commonly known CRUD APIs
- same principle is used in REST APIs and several other types of APIs
- not all APIs work in the same way and the user access  control will limit what actions we can perform and what result we can see

#### Read
- first thing we will do when interacting with an API is reading data
- we can specify the table name after the API (e.g. /table_name) and specify our search term (e.g. /name) 
- ```
  curl http;//serverip:port/api.php/table_name/search_term
  ```
![[Pasted image 20260514210703.png]]

- we can see that the result is sent as a JSON string
- to have it properly formatted in JSON format, we can  pipe the output to the jq utility which will format it properly
![[Pasted image 20260514210836.png]]

- we can see the output in nicely formatted output
- we can provide search term and get all matching result
![[Pasted image 20260514211007.png]]

- we can pass an empty string to retreive all entries in table 
  ![[Pasted image 20260514211114.png]]
- we can see the rendered result in browser
![[Pasted image 20260514211334.png]]



#### Create
- to add a new entry, we can use an HTTP POST request, which is similar to what we have performed in the previous section
- we can simply POST our JSON data, and it will be added to the table. 
- As API is using JSON data, we will also set the `Content-Type` header to JSON

```
curl -X POST http://154.57.164.82:31901/api.php/city -d '{"city_name":"Hello","country_name":"HTB"}' -H 'Content-Type:application/json'
```

![[Pasted image 20260514212748.png]]

- we can read the content of  the city we added
- as we can see a new city was created which did not exist before

Exercise
- adding city through browser devtool by using one of the Fetch POST request
```
await fetch("http://154.57.164.72:30931/api.php/city", {
    credentials: "include",
    headers: {
        "Accept": "*/*",
        "Accept-Language": "en-US,en;q=0.5",
        "Content-Type": "application/json",
        "Sec-GPC": "1",
        "Priority": "u=0"
    },
    referrer: "http://154.57.164.74:30931/",
    body: JSON.stringify({
        city_name: "Hello56",
        country_name: "HTB"
    }),
    method: "POST",
    mode: "cors"
});
```

### Update
