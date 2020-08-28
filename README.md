# Table of content
- [Admin microservice](#Admin-microservice)
- [CFT (cubic feet)](#CFT-(cubic-feet))
	 * [Service name](#service-name-cft)
	 * [Base URL](#base-url-cft)
	 *  [Endpoints](#endpoints-cft)
	    + [GET](#get-cft)


# Admin microservice

  

# CFT (cubic feet)
<a name="service-name-cft"></a>
**Service name:** cft
<a name="base-url-cft"></a>
**Base URL:** [http://cft/api/cft](http://cft/api/cft/)
<a name="endpoints-cft"></a>
 **Endpoints:**
<a name="get-cft"></a>
- **GET:**
	 -   **Get all:**

		 - **Url:** base_url + /

		  - **Description:** Get all the carriers saved in the database from the cft
	   table.
	   
		   - **Path params:** None
	   
		   - **Query params:** None
	   
		   - **Request body:** None
	   
		   - **Responses:**
	   
			   - **404** - If no carrier is found.
```json
[
    {
        "broker_id":0,
        "carrier_id":0,
        "lower_limit":[
            0
        ],
        "upper_limit":[
            0
        ],
        "fee":[
            0
        ],
        "is_active":false,
        "id":0
    }
]
```
