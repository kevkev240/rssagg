# RSS Aggregator Project from freeCodeCamp golang Course

A backend server for RSS feeds aggregator using `golang`.

The database stores `users`, `feeds`, `feed_follows`, and `posts`. 

`scraper.go` periodically search and insert new posts into `posts` from the RSS feeds in `feeds`.

## API Documentation

All the authenticaed endpoint requires `Authorization: ApiKey ${APIKey}}` in the http request header.

------
**Create User**

Returns json data about a created user.

* **URL**

  /users

* **Method:**
  
  `POST`

* **Data Params**

  Body: `{"name": "Gerald"}`

* **Success Response:**

  * **Code:** 201 <br />
    **Content:** Inserted user entrie in json format with APIKey included.

 ------
**Get User**

Returns json data about a user. Authenticated with APIKey.

* **URL**

  /users

* **Method:**
  
  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** Corresponding user entrie in json format.

------
**Create Feed**

Returns json data about a created feed.

* **URL**

  /feeds

* **Method:**
  
  `POST`

* **Data Params**

  Body: `{"name": "Blog", "url": "https://blog.com/index.xml"}`

* **Success Response:**

  * **Code:** 201 <br />
    **Content:** Inserted feed entrie in json format.

------
**Get Feed**

Returns an array of feeds in json format.

* **URL**

  /feeds

* **Method:**
  
  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** An array of all feeds in json format from `feeds`.

------
**Get Posts**

Returns an array of at most 10 most recent posts by published time from all the feeds a user follows. Authenticated with APIKey.

* **URL**

  /posts

* **Method:**
  
  `GET`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** An array of posts in json format.

------
**Follow a Feed**

Returns json data about a created tuple in `feed_follows` table. Authenticated with APIKey.

* **URL**

  /feed_follows

* **Method:**
  
  `POST`

* **Data Params**

  Body: `{"feed_id": ${feed_id_to_follow}"}`

* **Success Response:**

  * **Code:** 201 <br />
    **Content:** A feed_follows tuple in json format.

------
**Get Followed Feeds**

Returns an array of feeds the user follows. Authenticated with APIKey.

* **URL**

  /feed_follows

* **Method:**
  
  `POST`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** An array of feed_follows that with the user as the follower, in json format.

------
**Unfollow a Feed**

Returns an array of feeds the user follows. Authenticated with APIKey.

* **URL**

  /feed_follows/{feedFollowID}

*  **URL Params**

   **Required:**
 
   `feedFollowID=[id for the feed_follow to be deleted]`

* **Method:**
  
  `DELETE`

* **Success Response:**

  * **Code:** 200 <br />

