## ***Постмaн***
## ***Примеры работ***
___
Приложение 1.
```json
{
	"info": {
		"_postman_id": "fc352e99-037f-40f6-8d18-8773631d6950",
		"name": "RestApi",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "20459192"
	},
	"item": [
		{
			"name": "GetBooking",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"protocolProfileBehavior": {
				"disableBodyPruning": true
			},
			"request": {
				"method": "GET",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://restful-booker.herokuapp.com/booking/{{bookingid}}",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"booking",
						"{{bookingid}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "CreateToken",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"var jsonToken = pm.response.json();\r",
							"pm.collectionVariables.set(\"token\", jsonToken.token);"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"username\" : \"admin\",\r\n    \"password\" : \"password123\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://restful-booker.herokuapp.com/auth",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"auth"
					]
				}
			},
			"response": []
		},
		{
			"name": "UpdateBooking",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "PUT",
				"header": [
					{
						"key": "Cookie",
						"value": "token = {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"firstname\" : \"James\",\r\n    \"lastname\" : \"Brown\",\r\n    \"totalprice\" : 111,\r\n    \"depositpaid\" : true,\r\n    \"bookingdates\" : {\r\n        \"checkin\" : \"2018-01-01\",\r\n        \"checkout\" : \"2019-01-01\"\r\n    },\r\n    \"additionalneeds\" : \"Breakfast\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://restful-booker.herokuapp.com/booking/{{bookingid}}",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"booking",
						"{{bookingid}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "CreateBooking",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"var jsonData = pm.response.json();\r",
							"pm.collectionVariables.set(\"bookingid\", jsonData.bookingid);"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"firstname\" : \"Jim\",\r\n    \"lastname\" : \"Brown\",\r\n    \"totalprice\" : 111,\r\n    \"depositpaid\" : true,\r\n    \"bookingdates\" : {\r\n        \"checkin\" : \"2018-01-01\",\r\n        \"checkout\" : \"2019-01-01\"\r\n    },\r\n    \"additionalneeds\" : \"Breakfast\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://restful-booker.herokuapp.com/booking",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"booking"
					]
				}
			},
			"response": []
		},
		{
			"name": "PartialUpdateBooking",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "PATCH",
				"header": [
					{
						"key": "Cookie",
						"value": "token = {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"firstname\" : \"James\",\r\n    \"lastname\" : \"Brown\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "https://restful-booker.herokuapp.com/booking/{{bookingid}}",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"booking",
						"{{bookingid}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "DeleteBooking",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "DELETE",
				"header": [
					{
						"key": "Cookie",
						"value": "token = {{token}}",
						"type": "text"
					}
				],
				"url": {
					"raw": "https://restful-booker.herokuapp.com/booking/{{bookingid}}",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"booking",
						"{{bookingid}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "HealthCheck",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"protocolProfileBehavior": {
				"disableBodyPruning": true
			},
			"request": {
				"method": "GET",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": ""
				},
				"url": {
					"raw": "https://restful-booker.herokuapp.com/ping",
					"protocol": "https",
					"host": [
						"restful-booker",
						"herokuapp",
						"com"
					],
					"path": [
						"ping"
					]
				}
			},
			"response": []
		}
	],
	"event": [
		{
			"listen": "prerequest",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		},
		{
			"listen": "test",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		}
	],
	"variable": [
		{
			"key": "bookingid",
			"value": "",
			"type": "string"
		},
		{
			"key": "token",
			"value": "",
			"type": "string"
		}
	]
}
```

Приложение 2
___
Post
```json
{
	"info": {
		"_postman_id": "aea19f00-83ab-4d13-b877-1f605d6c9516",
		"name": "Spoonacular API post Homework",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "20459192"
	},
	"item": [
		{
			"name": "Classify Cuisine ingredientList",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Mediterranean\");\r",
							"});\r",
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Pork roast with green beans",
							"type": "text"
						},
						{
							"key": "ingredientList",
							"value": "3 oz pork shoulder",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine burger",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Middle Eastern\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Falafel Burger",
							"type": "text"
						},
						{
							"key": "ingredientList",
							"value": "1 cup green tea",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine Broccolini Quinoa Pilaf",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Mediterranean\");\r",
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200,202]);\r",
							"});\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Broccolini Quinoa Pilaf",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine Cauliflower, Brown Rice, and Vegetable Fried Rice",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Chinese\");\r",
							"});\r",
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Cauliflower, Brown Rice, and Vegetable Fried Rice",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine Homemade Garlic and Basil French Fries",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"American\");\r",
							"});\r",
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Homemade Garlic and Basil French Fries",
							"type": "text"
						},
						{
							"key": "language",
							"value": "de",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine Berry Banana Breakfast Smoothie",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Mediterranean\");\r",
							"});\r",
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Berry Banana Breakfast Smoothie",
							"type": "text"
						},
						{
							"key": "language",
							"value": "de",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine negative",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(401);\r",
							"});\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"failure\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Dark Chocolate Mousse",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine Roasted Asparagus",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Mediterranean\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Roasted Asparagus",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine Crockpot Cashew Chicke",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"European\");\r",
							"});\r",
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "Crockpot Cashew Chicke",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Classify Cuisine $50,000 Burger",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Successful POST request\", function () {\r",
							"    pm.expect(pm.response.code).to.be.oneOf([200, 202]);\r",
							"});\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"American\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "urlencoded",
					"urlencoded": [
						{
							"key": "title",
							"value": "$50,000 Burger",
							"type": "text"
						},
						{
							"key": "language",
							"value": "en",
							"type": "text"
						}
					]
				},
				"url": {
					"raw": "{{baseURLpost}}",
					"host": [
						"{{baseURLpost}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "New Request",
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n\t\"item\": \"1 package baking powder\",\r\n\t\"aisle\": \"Baking\",\r\n\t\"parse\": true\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{baseURL}}/mealplanner/username=your-users-name591/shopping-list/items?&hash=000f62c7eaa04bf4ac04d8bd163dd91544d11cfa",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"mealplanner",
						"username=your-users-name591",
						"shopping-list",
						"items"
					],
					"query": [
						{
							"key": null,
							"value": null
						},
						{
							"key": "hash",
							"value": "000f62c7eaa04bf4ac04d8bd163dd91544d11cfa"
						}
					]
				}
			},
			"response": []
		}
	],
	"event": [
		{
			"listen": "prerequest",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		},
		{
			"listen": "test",
			"script": {
				"type": "text/javascript",
				"exec": [
					"pm.test(\"Response time is less than 200ms\", function () {",
					"    pm.expect(pm.response.responseTime).to.be.below(400);",
					"});",
					"pm.test(\"Content-Type is present\", function () {",
					"    pm.response.to.have.header(\"Content-Type\");",
					"});",
					""
				]
			}
		}
	]
}
```
GET
```json
{
	"info": {
		"_postman_id": "033e9c4e-b9f9-4ee9-a4a5-f35877a009a3",
		"name": "Spoonacular API get Homework",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "20459192"
	},
	"item": [
		{
			"name": "Search Recipes burger",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Falafel Burger\");\r",
							"});\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?query=burger",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "query",
							"value": "burger"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes pasta",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Pasta With Tuna\");\r",
							"});\r",
							"\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?query=pasta",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "query",
							"value": "pasta"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes italian",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"\r",
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Broccolini Quinoa Pilaf\");\r",
							"});\r",
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"auth": {
					"type": "apikey",
					"apikey": [
						{
							"key": "key",
							"value": "apiKey",
							"type": "string"
						},
						{
							"key": "in",
							"value": "query",
							"type": "string"
						},
						{
							"key": "value",
							"value": "209d9d4b2e214928bdb6adea0bac819a",
							"type": "string"
						}
					]
				},
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?cuisine=italian",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "cuisine",
							"value": "italian"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes greek",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Cauliflower, Brown Rice, and Vegetable Fried Rice\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?excludeCuisine=greek",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "excludeCuisine",
							"value": "greek"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes vegetarian",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Cauliflower, Brown Rice, and Vegetable Fried Rice\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?diet=vegetarian",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "diet",
							"value": "vegetarian"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes gluten",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Cauliflower, Brown Rice, and Vegetable Fried Rice\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?intolerances=gluten",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "intolerances",
							"value": "gluten"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes pan",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Broccoli and Chickpea Rice Salad\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?equipment=pan",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "equipment",
							"value": "pan"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes minFat",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Homemade Garlic and Basil French Fries\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?minFat=1",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "minFat",
							"value": "1"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes tomato,cheese",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Spinach N Walnut Stuffed Mushrooms\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?includeIngredients=tomato,cheese",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "includeIngredients",
							"value": "tomato,cheese"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes eggs",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"African Chicken Peanut Stew\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?excludeIngredients=eggs",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "excludeIngredients",
							"value": "eggs"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes main course",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Slow Cooker Beef Stew\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?type=main course",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "type",
							"value": "main course"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes instructionsRequired",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Broccoli and Chickpea Rice Salad\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?instructionsRequired=true",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "instructionsRequired",
							"value": "true"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes maxSugar",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Berry Banana Breakfast Smoothie\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?maxSugar=100",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "maxSugar",
							"value": "100"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes fillIngredients",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Red Kidney Bean Jambalaya\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?fillIngredients=false",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "fillIngredients",
							"value": "false"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes coffeebean",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Roasted Asparagus\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?author=coffeebean",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "author",
							"value": "coffeebean"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes myCustomTag",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Nigerian Snail Stew\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?tags=myCustomTag",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "tags",
							"value": "myCustomTag"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes recipeBoxId",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Dark Chocolate Mousse\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?recipeBoxId=2468",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "recipeBoxId",
							"value": "2468"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes Crock Pot",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"How to Make the Best Crock Pot Roas\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?titleMatch=Crock Pot",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "titleMatch",
							"value": "Crock Pot"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes calories",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"Kim's Baked Macaroni & Cheese\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?sort=calories",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "sort",
							"value": "calories"
						}
					]
				}
			},
			"response": []
		},
		{
			"name": "Search Recipes asc",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Body matches string\", function () {\r",
							"    pm.expect(pm.response.text()).to.include(\"5-minute Ricotta Garlic Herb Dip\");\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{baseURL}}/recipes/complexSearch?sortDirection=asc",
					"host": [
						"{{baseURL}}"
					],
					"path": [
						"recipes",
						"complexSearch"
					],
					"query": [
						{
							"key": "sortDirection",
							"value": "asc"
						}
					]
				}
			},
			"response": []
		}
	],
	"auth": {
		"type": "apikey",
		"apikey": [
			{
				"key": "value",
				"value": "209d9d4b2e214928bdb6adea0bac819a",
				"type": "string"
			},
			{
				"key": "key",
				"value": "apiKey",
				"type": "string"
			},
			{
				"key": "in",
				"value": "query",
				"type": "string"
			}
		]
	},
	"event": [
		{
			"listen": "prerequest",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		},
		{
			"listen": "test",
			"script": {
				"type": "text/javascript",
				"exec": [
					"pm.test(\"Status code is 200\", function () {",
					"    pm.response.to.have.status(200);",
					"});",
					"pm.test(\"Content-Type is present\", function () {",
					"    pm.response.to.have.header(\"Content-Type\");",
					"});",
					"pm.test(\"Response time is less than 200ms\", function () {",
					"    pm.expect(pm.response.responseTime).to.be.below(500);",
					"});",
					""
				]
			}
		}
	],
	"variable": [
		{
			"key": "baseURL",
			"value": "https://api.spoonacular.com",
			"type": "string"
		}
	]
}
```
___
Environment
```json
{
	"id": "bb269f1e-b7dc-4677-bd9f-4c2d7da8e91c",
	"name": "Environments Spoonacular API",
	"values": [
		{
			"key": "baseURL",
			"value": "https://api.spoonacular.com",
			"type": "default",
			"enabled": true
		},
		{
			"key": "Email",
			"value": "edgar.nurmagomedov@mail.ru",
			"type": "default",
			"enabled": true
		},
		{
			"key": "API-key",
			"value": "209d9d4b2e214928bdb6adea0bac819a",
			"type": "secret",
			"enabled": true
		},
		{
			"key": "baseURLpost",
			"value": "https://api.spoonacular.com/recipes/cuisine",
			"type": "default",
			"enabled": true
		}
	],
	"_postman_variable_scope": "environment",
	"_postman_exported_at": "2023-06-17T15:19:52.338Z",
	"_postman_exported_using": "Postman/10.14.9"
}
```