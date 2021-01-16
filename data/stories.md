## actual story: happy path
* greet
    - utter_greet
* restaurant_search
    - utter_ask_location
* restaurant_search{"location": "delhi"}
    - slot{"location": "delhi"}
    - action_check_location
    - slot{"location_ok": "True"}
    - utter_ask_cuisine
* restaurant_search{"cuisine": "chinese"}
    - slot{"cuisine": "chinese"}
    - action_check_cuisine
    - slot{"cuisine_ok": "True"}
    - utter_ask_budget
* restaurant_search{"budget":"mid"}
    - action_check_budget
    - slot{"budget_ok": "True"}
    - action_search_restaurants
    - utter_ask_email
* affirm
    - utter_ask_email_id
* sendemail{"email": "xyz@test.com"}
	- slot{"email": "xyz@test.com"}
	- action_validate_email
	- slot{"email": "xyz@test.com"}
	- action_send_email
	- utter_goodbye
    - export

## when location is wrong
* greet
    - utter_greet
* restaurant_search{"location": "bluru"}
    - slot{"location": "bluru"}
    - action_check_location
    - slot{"location": null}
    - slot{"location_ok": false}
    - utter_notavailable
    - utter_goodbye
    - export

## when location is right
* restaurant_search{"location": "Kolkata"}
    - slot{"location": "Kolkata"}
    - action_check_location
    - slot{"location": "Kolkata"}
    - slot{"location_ok": true}
    - utter_ask_cuisine
* restaurant_search{"cuisine": "north indian"}
    - slot{"cuisine": "north indian"}
    - action_check_cuisine
    - slot{"cuisine": "north indian"}
    - slot{"cuisine_ok": true}
    - utter_ask_budget
* restaurant_search{"budget": "700"}
    - slot{"budget": "700"}
    - action_check_budget
    - slot{"budget": "mid"}
    - slot{"budget_ok": true}
    - action_search_restaurants
    - utter_goodbye
    - export

## when location is wrong more than once
* greet
    - utter_greet
* restaurant_search{"location": "spain"}
    - slot{"location": "spain"}
    - action_check_location
    - slot{"location": null}
    - slot{"location_ok": false}
    - utter_notavailable
    - utter_ask_location
* restaurant_search{"location": "Delhi NCR"}
    - slot{"location": "Delhi NCR"}
    - action_check_location
    - slot{"location": null}
    - slot{"location_ok": false}
    - utter_goodbye
    - export 

## When given cuisine is not valid
* greet
    - utter_greet
* restaurant_search{"location": "kolkata", "cuisine": "thai"}
    - slot{"cuisine": "thai"}
    - slot{"location": "kolkata"}
    - action_check_location
    - slot{"location": "kolkata"}
    - slot{"location_ok": true}
    - action_check_cuisine
    - slot{"cuisine": null}
    - slot{"cuisine_ok": false}
    - utter_ask_cuisine
* restaurant_search{"cuisine": "korean"}
    - slot{"cuisine": "korean"}
    - action_check_cuisine
    - slot{"cuisine": null}
    - slot{"cuisine_ok": false}
    - utter_goodbye 
    - export

## When user enters the correct details
* restaurant_search{"location": "pune"}
    - slot{"location": "pune"}
    - action_check_location
    - slot{"location": "pune"}
    - slot{"location_ok": true}
    - utter_ask_cuisine
* restaurant_search{"cuisine": "chinese"}
    - slot{"cuisine": "chinese"}
    - action_check_cuisine
    - slot{"cuisine": "chinese"}
    - slot{"cuisine_ok": true}
    - utter_ask_budget
* restaurant_search{"budget": "More than 700"}
    - slot{"budget": "More than 700"}
    - action_check_budget
    - slot{"budget": "high"}
    - slot{"budget_ok": true}
    - action_search_restaurants
    - slot{"budget": "high"}
    - utter_ask_email
* sendemail{"email": "adyasha.rath@gmail.com"}
    - slot{"email": "adyasha.rath@gmail.com"}
    - action_validate_email
    - slot{"email": "adyasha.rath@gmail.com"}
    - action_send_email
    - slot{"email": "adyasha.rath@gmail.com"}
    - utter_goodbye
    - export

## when user enters an invalid email id
* greet
    - utter_greet
* restaurant_search{"cuisine": "chinese", "location": "pune"}
    - slot{"cuisine": "chinese"}
    - slot{"location": "pune"}
    - action_check_location
    - slot{"location": "pune"}
    - slot{"location_ok": true}
    - action_check_cuisine
    - slot{"cuisine": "chinese"}
    - slot{"cuisine_ok": true}
    - utter_ask_budget
* restaurant_search{"budget": "More than 700"}
    - slot{"budget": "More than 700"}
    - action_check_budget
    - slot{"budget": "high"}
    - slot{"budget_ok": true}
    - action_search_restaurants
    - slot{"budget": "high"}
    - utter_ask_email
* affirm
    - utter_ask_email_id
* sendemail{"email": "hgjjh"}
    - slot{"email": "hgjjh"}
    - action_validate_email
    - slot{"email": null}
    - action_send_email
    - utter_ask_email
* affirm
    - utter_ask_email_id
* sendemail{"email": "binny.garg9@gmail.com"}
    - slot{"email": "binny.garg9@gmail.com"}
    - action_validate_email
    - slot{"email": "binny.garg9@gmail.com"}
    - action_send_email
    - slot{"email": "binny.garg9@gmail.com"}
    - utter_goodbye
    - export



