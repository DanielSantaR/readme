


# Table of content
- [Admin microservice](#Admin-microservice)
- [Standard microservices](#standard-microservices)
	 * [Service name](#service-name-standard)
	 * [Base URL](#base-url-standard)
	 *  [Endpoints](#endpoints-standard)
	    + [GET](#get-standard)
	    + [POST](#post-standard)
	    + [PUT](#put-standard)
	    + [DELETE](#delete-standard)
- [Accessorial microservice](#accessorial-microservices)
	 * [Service name](#service-name-accessorial)
	 * [Base URL](#base-url-accessorial)
	 *  [Endpoints](#endpoints-accessorial)
	    + [GET](#get-accessorial)
	    + [POST](#post-accessorial)
	    + [PUT](#put-accessorial)
	    + [DELETE](#delete-accessorial)

# Admin microservice

  

# Standard microservices
<a name="service-name-standard"></a>
**Services names:** cubic-capacity, height, width, length-per-piece, single-shipment, pieces, cft, weight-per-piece, total-weight, liftgate-weight.

<a name="base-url-standard"></a>
**Base URL:** [http://BR-service-name/api/BR-service-name](http://BR-service-name/api/BR-service-name/)

<a name="endpoints-standard"></a>
 **Endpoints:**
 
<a name="get-standard"></a>
 - **GET:**
	 -   **Get all:**

		 - **Url:** `base_url + /`

		  - **Description:** Get all the carriers saved in the database from the business rule
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

		  - **Description:** get the fees of a specific carrier for the business rule
	   
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

<a name="post-standard"></a>
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
			

			---

			**Note:** The upper_limit, lower_limit and fee arrangements must be the same size.
			
			---

	   
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
			**Restriction:** The entity as it comes in the quotation after being standardized.
	
			- **cubic-capacity:**  Get the cubic feet, e.g: "10 cft".
			- **height:** Get the dimension of the piece, e. g: "48x48x48 inches"
			- **width:** Get the dimension of the piece, e. g: "48x48x48 inches"
			- **length-per-piece:** Get the dimension of the piece, e. g: "48x48x48 inches"
			- **single-shipment:** Get the weight of the load, e. g: "200 lbs"
			- **pieces:** Get the pieces of the load, e. g: "5 pallets"
			- **cft:** Get the cubic feet, e.g: "10 cft".
			- **weight-per-piece:** Get the weight of the piece, e. g: "200 lbs"
			- **total-weight:** Get the weight of the load, e. g: "200 lbs"
			- **liftgate-weight:** Get the weight of the piece, e. g: "200 lbs"

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

<a name="put-standard"></a>
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
			
			---

			**Note:** The upper_limit, lower_limit and fee arrangements must be the same size.
			
			---
	   
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

<a name="delete-standard"></a>
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

# Accessorials microservice
<a name="service-name-accessorial"></a>
**Service name:** accessorial.

<a name="base-url-accessorial"></a>
**Base URL:** [http://accessorial/api/accessorial](http://accessorial/api/accessorial/)

<a name="endpoints-accessorial"></a>
 **Endpoints:**
 
<a name="get-accessorial"></a>
 - **GET:**
	 -   **Get all:**

		 - **Url:** `base_url + /`

		  - **Description:** Get all the carriers saved in the database from the business rule
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
					    "broker_id": 0,
					    "carrier_id": 0,
					    "accessorial": "string",
					    "can_move": true,
					    "fee": 0,
					    "is_active": false,
					    "id": 0
					  }
					]
					```
	 -   **Get by id:**

		 - **Url:** `base_url + /{broker_id}/{carrier_id}/{accessorial}`

		  - **Description:** get a carrier from a broker through the ids of both.
	   
		   - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
				- accessorial - str
	   
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
					  "broker_id": 0,
					  "carrier_id": 0,
					  "accessorial": "string",
					  "can_move": true,
					  "fee": 0,
					  "is_active": false,
					  "id": 0
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
	 
		 - **Url:** `base_url + /get_fees/{broker_id}/{carrier_id}/{accessorial}`

		  - **Description:** get the fees of a specific carrier for the business rule
	   
		  - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
				- accessorial - str
	   
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
					  "accessorial": "string",
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

<a name="post-accessorial"></a>
 - **POST:**
	 -   **Create:**

		 - **Url:** `base_url + /`

		  - **Description:** Create a new carrier 
	   
		   - **Path params:** None
	   
		   - **Query params:** None
	   
		   - **Request body:** 
			```json
			{
			  "broker_id": 0,
			  "carrier_id": 0,
			  "accessorial": "string",
			  "can_move": true,
			  "fee": 0,
			  "is_active": false
			}
			```
				
			**Broker_id:** Integer, greater or equal than 0. 
			
			**Carrier_id:** Integer, greater or equal than 0.
			
			**Accessorial:** Str.

			**Can_move:** Boolean.
			
			**Fee:** List of floats, greater than zero, representing all the rates for the ranges defined above.
			
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
				- **201** - If the carrier is created successfully.
				
					**Eschema:**
					```json
					{
					  "broker_id": 0,
					  "carrier_id": 0,
					  "accessorial": "string",
					  "can_move": true,
					  "fee": 0,
					  "is_active": false,
					  "id": 0
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
			  "id": 0,
			  "broker_id": 0,
			  "carrier_id": 0,
			  "accessorial": "string",
			  "can_move": true,
			  "fee": 0,
			  "is_active": true
			}
			```
			**id:**  Unique ID for a broker's carrier in the business rule. Integer greater or equal than 0.
			
			**Broker_id:** Integer, greater or equal than 0. 
			
			**Carrier_id:** Integer, greater or equal than 0.

			**Accessoial:** Str.

			**can_move:** Boolean.
			
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
			**Restriction:** The entity as it comes in the quotation after being standardized. E. g: "TSA", "Airport Pickup", etc. 

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
				  "available_carriers": [
				    {
				      "broker_id": 0,
				      "carrier_id": 0,
				      "accessorial": "string",
				      "fee": 0
				    }
				  ],
				  "exclude_lower_carriers": [
				    {
				      "broker_id": 0,
				      "carrier_id": 0,
				      "accessorial": "string",
				      "message": "Carrier cannot move loads with the accessorial"
				    }
				  ],
				  "exclude_upper_carriers": [
				    {}
				  ]
				}
					```

<a name="put-accessorial"></a>
 - **PUT:**
	 -   **Update:**

		 - **Url:** `base_url + /{broker_id}/{carrier_id}/{accessorial}`

		  - **Description:** Update a carrier
	   
		   - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
				- accessorial - str.
	   
		   - **Query params:** None
	   
		   - **Request body:** 
			```json
			{
			  "can_move": true,
			  "fee": 0,
			  "is_active": true
			}
			```

			**Can_move:** Boolean, False if the carrier cannot move the load and true if he can move it.
			
			**Fee:** List of floats, greater than zero, representing all the rates for the ranges defined above.
			
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
				- **200** -   Carrier updated.
				
					**Eschema:**
					```json
					{
					  "can_move": true,
					  "fee": 0,
					  "is_active": true
					}
					```

				- **404** -     Carrier not found.
				
					**Eschema:**
					```json
					{
					    "detail":"No carrier found"
					}
					```

<a name="delete-accessorial"></a>
 - **DELETE:**
	 -   **Remove:**

		 - **Url:** `base_url + /{broker_id}/{carrier_id}/{accessorial}`

		  - **Description:** Delete a carrier
	   
		   - **Path params:** 
				- broker_id - integer, minimum zero.
				- carrier_id - integer, minimum zero.
				- accessorial - str.
	   
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
