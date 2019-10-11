# OpenAPI Specification for a members API
This is the OpenAPI specification for a very simple members API.

## Background
The idea behind this API is to create a very simple list of family members which than can be used to e.g. create a family memory game.

## Model
Currently a **member** consists of the following model (example):

```json
{
  "name": "Luke Skywalker",
  "description": "The young man, called to adventure, the hero going out facing the trials and ordeals, and coming back after his victory with a boon for the community",
  "image": "https://upload.wikimedia.org/wikipedia/en/9/9b/Luke_Skywalker.png"
}
```

### Response models
Responses are namespaced and the actual data is ... in a **data** attribute. 
With the namespaced approach all responses leave room for extensions in the future without
breaking the actual model.

#### Identifier 
All response models include an **id** property (**uuid** string) which will be generatede
from the system automatically. The **id** can not be included in any request model. 

#### Collection response
The collection response of the `GET /members` endpoint looks like:

````json
{
  "data": [
    {   
      "id": "3e3e9ec9-6267-4d42-b5fa-836d7e758625",
      "name": "Luke Skywalker",
      "description": "The young man, called to adventure, the hero going out facing the trials and ordeals, and coming back after his victory with a boon for the community",
      "image": "https://upload.wikimedia.org/wikipedia/en/9/9b/Luke_Skywalker.png"
    },
    {   
      "id": "492bb9fe-a79e-46fa-bf14-4bde44edf7a7",
      "name": "Darth Vader",
      "description": "Once a heroic Jedi Knight, Darth Vader was seduced by the dark side of the Force, became a Sith Lord, and led the Empire’s eradication of the Jedi Order. He remained in service of the Emperor -- the evil Darth Sidious -- for decades, enforcing his Master’s will and seeking to crush the fledgling Rebel Alliance. But there was still good in him…",
      "image": "https://upload.wikimedia.org/wikipedia/en/7/76/Darth_Vader.jpg"
    }
  ],
  "meta": {
    "pagination": {
      "page": 3,
      "count": 263,
      "total": 1263,
      "limit": 500
    }
  }
}   

```` 

#### Item response
The item response of the `GET /members/{memberId}` endpoint looks like:

````json
{
  "data": {   
      "id": "3e3e9ec9-6267-4d42-b5fa-836d7e758625",
      "name": "Luke Skywalker",
      "description": "The young man, called to adventure, the hero going out facing the trials and ordeals, and coming back after his victory with a boon for the community",
      "image": "https://upload.wikimedia.org/wikipedia/en/9/9b/Luke_Skywalker.png"
  }
}   
````

### Request models
The request model is the same as the member core model [reference/members/models/member/member.v1.json]:

````json
{   
  "name": "Luke Skywalker",
  "description": "The young man, called to adventure, the hero going out facing the trials and ordeals, and coming back after his victory with a boon for the community",
  "image": "https://upload.wikimedia.org/wikipedia/en/9/9b/Luke_Skywalker.png"
}   
````
