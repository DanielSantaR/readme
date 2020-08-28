
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

		 - **Url:** `base_url + /`

		  - **Description:** Get all the carriers saved in the database from the cft
	   table.
	   
		   - **Path params:** None
	   
		   - **Query params:** None
	   
		   - **Request body:** None
	   
		   - **Responses:**
	   
			   - **404** - If no carrier is found.
			   
				   	**Eschema:**
					```json
					{
					    "detail":"No carriers found"
					}
					```
				- **200** - If at least one carrier is found, return a list with the carriers found.
				
					**Eschema:**
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
	 -   **Get by id:**

		 - **Url:** `base_url + /{broker_id}/{carrier_id}`

		  - **Description:** **get a carrier from a broker through the ids of both.**
	   
		   - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
	   
		   - **Query params:** None
	   
		   - **Request body:** None
	   
		   - **Responses:**
			   - **404** - If no carrier is found.
			   
				   	**Eschema:**
					```json
					{
					  "detail":"No carrier found"
					}
					```
