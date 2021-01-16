
## interactive_story_1
* greet
    - utter_greet
* restaurant_search{"cuisine": "chinese", "location": "delhi"}
    - slot{"cuisine": "chinese"}
    - slot{"location": "delhi"}
    - action_check_location
    - slot{"location": "delhi"}
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
* sendemail{"email": "adyasha016@gmail.com"}
    - slot{"email": "adyasha016@gmail.com"}
    - action_validate_email
    - slot{"email": "adyasha016@gmail.com"}
    - action_send_email
    - slot{"email": "adyasha016@gmail.com"}
    - utter_goodbye
