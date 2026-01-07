
# {{ NAME }} Route Design Recipe

_Copy this design recipe template to test-drive a plain-text Flask route._

## 1. Design the Route Signature

_Include the HTTP method, the path, and any query or body parameters._

```

POST /albums
    title: string
    release_year: int
    artist_id: int
```

## 2. Create Examples as Tests

_Go through each route and write down one or more example responses._

_Remember to try out different parameter values._

_Include the status code and the response body._

```python

# POST /albums
#  Parameters:
#    title: Gold
#    release_year: 1992
#    artist_id: 2
#  Expected response (200 OK):
"""
"""

# GET /albums
# Expected response (200 OK):
"""
Album(1, "Doolittle", 1989, 1)
Album(2, "Surfer Rosa", 1988, 1)
Album(3, "Waterloo", 1974, 2)
Album(4, "Super Trouper", 1980, 2)
Album(5, "Bossanova", 1990, 1)
Album(6, "Lover", 2019, 3)
Album(7, "Folklore", 2020, 3)
Album(8, "I Put a Spell on You", 1965, 4)
Album(9, "Baltimore", 1978, 4)
Album(10, "Here Comes the Sun",1971, 4)
Album(11, "Fodder on My Wings", 1982, 4)
Album(12, "Ring Ring", 1973, 2)
Album(13, "Gold", 1992, 2)
"""

# POST /albums
#  Expected response (400 Bad Request):
"""
Necessary album data expected
"""

```

## 3. Test-drive the Route

_After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour._

Here's an example for you to start with:

```python
"""
GET /home
  Expected response (200 OK):
  "This is my home page!"
"""
def test_get_home(web_client):
    response = web_client.get('/home')
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'This is my home page!'

"""
POST /submit
  Parameters:
    name: Leo
    message: Hello world
  Expected response (200 OK):
  "Thanks Leo, you sent this message: "Hello world""
"""
def test_post_submit(web_client):
    response = web_client.post('/submit', data={'name': 'Leo', 'message': 'Hello world'})
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'Thanks Leo, you sent this message: "Hello world"'
```

