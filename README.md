
# Table of content
- [Admin microservice](#Admin-microservice)
- [CFT (cubic feet)](#CFT-(cubic-feet))
	 * [Service name](#service-name-cft)
	 * [Base URL](#base-url-cft)
	 *  [Endpoints](#endpoints-cft)
	    + [GET](#get-cft)
	    + [POST](#post-cft)
	    + [PUT](#put-cft)
	    + [DELETE](#delete-cft)


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

		  - **Description:** get a carrier from a broker through the ids of both.
	   
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
				- **200** - If the carrier is found, return a dictionary with all the information.

					**Eschema:**
					```json
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
					```
				- **422** - Unprocessable entity.

					**Eschema**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```
			

	 - **Get fees:** 
		 - **Url:** `base_url + /get_fees/{broker_id}/{carrier_id}`

		  - **Description:** get the fees of a specific carrier for the cft rule
	   
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
				- **200** - If the carrier is found, return a dictionary with the fee.

					**Eschema:**
					```json
						{
						  "broker_id": 0,
						  "carrier_id": 0,
						  "fee": 0
						}
					```
				- **422** - Unprocessable entity.

					**Eschema**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```

<a name="post-cft"></a>
 - **POST:**
	 -   **Create:**

		 - **Url:** `base_url + /`

		  - **Description:** Create a new carrier 
	   
		   - **Path params:** None
	   
		   - **Query params:** None
	   
		   - **Request body:** 
			```json
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
			    "is_active":false
			}
			```
				
			**Broker_id:** Integer, greater or equal than 0. 
			**Carrier_id:** Integer, greater or equal than 0.
			**Lower_limit:** List of floats, greater than zero, that represent all the lower limits of the ranges for this rule.
			**Upper_limit:** List of floats, greater than zero, that represent all the upper limits of the ranges for this rule.
			**Fee:** List of floats, greater than zero, representing all the rates for the ranges defined above.
			**Is_active:** If for the quote the carrier must be evaluated in this business rule (True) or if it is included automatically (False).

			**Note:** The upper_limit, lower_limit and fee arrangements must be the same size.

	   
		   - **Responses:**
	   
			   - **422** - Unprocessable Entity.
			   
				   	**Eschema:**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```
				- **201** - If the carrier is created successfully.
				
					**Eschema:**
					```json
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
					```

	 -   **Count by fields:**

		 - **Url:** `base_url + /count/`

		  - **Description:** Count the carriers according to the fields sent.
	   
		   - **Path params:** None
	   
		   - **Query params:** None
	   
		   - **Request body:** 
			```json
			{
			    "id":0,
			    "broker_id":0,
			    "carrier_id":0,
			    "is_active":true
			}
			```
			**id:**  Unique ID for a broker's carrier in the business rule. Integer greater or equal than 0.
			**Broker_id:** Integer, greater or equal than 0. 
			**Carrier_id:** Integer, greater or equal than 0.
			**Is_active:** If for the quote the carrier must be evaluated in this business rule (True) or if it is included automatically (False).
	   
		   - **Responses:**
	   
			   - **422** - Unprocessable Entity.
			   
				   	**Eschema:**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```
				- **200** - Returns the total number of carriers that complied with the sent values.
				
					**Eschema:**
					```json
					0
					```

	 -   **Check carriers:**

		 - **Url:** `base_url + /check_carriers/`

		  - **Description:** Check the available carriers and excluded carriers according to the restriction.
	   
		   - **Path params:** None
	   
		   - **Query params:** None
	   
		   - **Request body:** 
			```json
			{
			    "restriction":"string",
			    "broker_id":0,
			    "carriers_id":[
			        null
			    ]
			}
			```
			**Restriction:** The entity as it comes in the quotation after being standardized. For example: "15 cft".
			**Broker_id:** Integer, greater or equal than 0. 
			**Carriers_id:** List of the carriers of a broker to be checked. List of integers, each one greater or equal than 0.
	   
		   - **Responses:**
	   
			   - **422** - Unprocessable Entity.
			   
				   	**Eschema:**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```
				- **200** - Carriers available and carriers excluded
				
					**Eschema:**
					```json
					{
					    "available_carriers":[
					        {
					            "broker_id":0,
					            "carrier_id":0,
					            "fee":0
					        }
					    ],
					    "exclude_lower_carriers":[
					        {
					            "broker_id":0,
					            "carrier_id":0,
					            "message":"<BR> smaller than the lower limit"
					        }
					    ],
					    "exclude_upper_carriers":[
					        {
					            "broker_id":0,
					            "carrier_id":0,
					            "message":"<BR> bigger than the upper limit"
					        }
					    ]
					}
					```

<a name="put-cft"></a>
 - **PUT:**
	 -   **Update:**

		 - **Url:** `base_url + /{broker_id}/{carrier_id}`

		  - **Description:** Update a carrier
	   
		   - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
	   
		   - **Query params:** None
	   
		   - **Request body:** 
			```json
			{
			    "lower_limit":[
			        0
			    ],
			    "upper_limit":[
			        0
			    ],
			    "fee":[
			        0
			    ],
			    "is_active":true
			}
			```

			**Lower_limit:** List of floats, greater than zero, that represent all the lower limits of the ranges for this rule.
			**Upper_limit:** List of floats, greater than zero, that represent all the upper limits of the ranges for this rule.
			**Fee:** List of floats, greater than zero, representing all the rates for the ranges defined above.
			**Is_active:** If for the quote the carrier must be evaluated in this business rule (True) or if it is included automatically (False).

			**Note:** The upper_limit, lower_limit and fee arrangements must be the same size.
	   
		   - **Responses:**
	   
			   - **422** - Unprocessable Entity.
			   
				   	**Eschema:**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```
				- **200** -   Carrier updated.
				
					**Eschema:**
					```json
					{
					    "lower_limit":[
					        0
					    ],
					    "upper_limit":[
					        0
					    ],
					    "fee":[
					        0
					    ],
					    "is_active":true
					}
					```

				- **404** -     Carrier not found.
				
					**Eschema:**
					```json
					{
					    "detail":"No carrier found"
					}
					```

<a name="delete-cft"></a>
 - **DELETE:**
	 -   **Remove:**

		 - **Url:** `base_url + /{broker_id}/{carrier_id}`

		  - **Description:** Delete a carrier
	   
		   - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
	   
		   - **Query params:** None
	   
		   - **Request body:** None
	   
		   - **Responses:**
	   
			   - **422** - Unprocessable Entity.
			   
				   	**Eschema:**
					```json
					{
					    "detail":[
					        {
					            "loc":[
					                "string"
					            ],
					            "msg":"string",
					            "type":"string"
					        }
					    ]
					}
					```
				- **204** -   Carrier deleted.
				
					**Eschema:** None

				- **404** -     Carrier not found.
				
					**Eschema:**
					```json
					0
					```
