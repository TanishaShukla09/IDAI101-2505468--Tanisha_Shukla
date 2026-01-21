# IDAI101-2505468--Tanisha_Shukla
NutriWell is a chatbot powered by Dialogflow that is meant to work as a personal wellness coach. It takes users on a journey to health and the use of features such as personalized workouts and diets, calorie-counter, and encouragement makes it easier. The bot identifies vital user information to give personalized advice and suggestions.


## Executive Summary

NutriWell AI Coach is a chat-based health coach, which helps people in the UK reach their health objectives by making them engage in a personalised interactive conversation. NutriWell was built with the Dialogflow Essentials in which customization of nutrition, hydration, exercising, and supplementation recommendations could be configured through modular payloads, entity-driven transitions, and context-sensitive flows.

This project is based on the logic of behavioural science and health priorities of the community, user-centre design. It partners to break down the obstacles to healthy living by providing sustainable, personalised and interactive online services especially to the groups which lack personalised coaching.

## Project Objectives

NutriWell objectives are as follows:

- To provide goal-focused health guidance in a conversational AI that will react to user-feedback.  
- Be able to support dietary profiling and hydration tracking in structured entities and rich payloads.  
- To provide an additional education in respect to UK health standards and customer needs.  
- Reminding, motivation prompts and follow-ups prompts are used to help the habit formation.  
- To support a later scalability and modularity to NHS or third-party integration.  
- All these targets demonstrate a concern with both technical and social health. NutriWell is not a chatbot; it is a duty as a digital companion that focuses on sustaining a sustainable change of behaviour.  

## Target Audience

NutriWell can be tailored to suit an enormously broad range of users in the UK:

**Targeted:** The young adults between the age of 18-60 years who require personal health advice.

- Individuals with dietary restrictions such as vegetarian, keto, or low GI.  
- Weight conscious, muscle building or generally fitness conscious individuals.  
- In a hurry, workers who must be reminded of themselves and fluids.  
- Health-conscious individuals in underserved or remote communities.  

NutriWell prides itself on the accessibility and flexibility whereby the individuals with different backgrounds will be involved in the health process.

## User Research & Survey Insights

One-hundred and twenty (120) participants in the UK of various ages and health background were surveyed structurally. The results influenced the NutriWell design on the layers.

- 72 percent of users desired goal-oriented meal plans. - diet-specific flows were designed and ShowMealPlanIntent.  
- 65% preferred chip-based UI over free text. - RichContent chip was introduced in all principal payloads.  
- 58% demanded hydration monitoring and notifications. HydrationIntent and SetReminderIntent were prioritised.  
- Recommendations of supplements had an interest among 54 percent. - The preview/full payloads were modularised.  
- 41% had dietary restrictions. - Tags such as @diettype were also mapped and also intents such vegdiet, ketodiet, etc.  
- It is based on these observations that the necessity of simplicity, personalisation and practical advice, which are the principles informing the NutriWell architecture, were proved.  

## Intent Architecture

NutriWell is contextual and modular in its conversational flow. Every state of output must have been determined beforehand by an intention which has as its consequence the successive step which secures the not only non-existence of friction, but also of smooth changes.

### Core Intents

#### Intents

**Default Intents**

- Default Fallback Intent: fills out any user request that does not find a matching intent.  
- Default Welcome Intent: Welcome, begin the chat.  
- MainMenuIntent: That is a connexion to the main options.  

**Goal & Profile Intents**

- GoalGainMuscleIntent: The intent of a user to gain muscle is noted.  
- GoalLoseWeightIntent: The intention defines the aim of a user to lose weight.  
- GoalMaintainWeightIntent: Goal type that describes the intention of a user to maintain his/her weight.  
- UserAgeIntent: It is applied to user age profile to issue personal advice.  
- UserGenderIntent: user gender profile exists.  
- WeightIntent: The user weight is defined.  

**Diet & Nutrition Intents**

- DietPreferenceIntent: Manages general dietary preferences.  
- ketodiet: the prescriptions of a ketogenic diet are addressed.  
- nonvegdiet: Manages non-vegetarian diet preferences.  
- paleodiet: Deals with the paleo diet.  
- vegdiet: Manages vegetarian diet preferences.  
- vegandiet: Retreats with a vegan diet.  
- ShowMealPlanIntent: demonstrates a single meal plan.  
- HydrationTipsIntent: This intent gives the advice on how to be hydrated.  
- SupplementSuggestionIntent: Offers suggestions for nutritional supplements.  

**Workout & Exercise Intents**

- Exercise TypeIntent: It is a field that stores a type of an exercise that the customer prefers.  
- CardioWorkoutIntent: Provides cardio exercise routines.  
- HIITWorkoutIntent: Provides High-intensity Interval Training (HIIT).  
- RunningWorkoutIntent: Provides running-specific workouts.  
- YogaWorkoutIntent: It is an application that provides yoga workout plans.  

## Entities

Entities are employed to get important information concerning the input of the user.

- @allergytype: Captures specific allergies (e.g., peanut, dairy, gluten).  
- @cookingskill: The user can save his/her cooking skill (e.g. beginner, expert).  
- @cuisine: Captures specific types of cuisine (e.g., Italian, Mexican).  
- @dietgoal: Records the users dietary objectives (e.g. low-carb, high-protein).  
- @exercisetype: Records the form of exercise (e.g., cardio, strength, yoga).  
- @foodpreference: General food preferences (i.e. spicy, sweet).  
- @gender: Records the gender of the user.  
- @ingredient: Captures specific food ingredients.  
- @mealtype: Meal type (e.g. breakfast, lunch, dinner).  
- @metricunit: Stores metric measures of weight or height (e.g. kg, cm).  
- @Supplements: Captures names of supplements (e.g., protein, creatine).  


## Conversation Flow Logic


- Default Welcome Intent  
    - GoalSetIntent  
        - UserGenderIntent  
            - UserAgeIntent  
                - UserWeightIntent  
                    - ShowMealPlanIntent  
                        - ExerciseIntent / HydrationIntent / HealthySnackIdeaIntent  
                            - SetReminderIntent


```json
## Payload Examples
Age Prompt Payload
json
{
  "richContent": [
    [
      {
        "type": "info",
        "title": "Thanks!",
        "subtitle": "How old are you? (This helps me calculate your needs accurately)."
      },
      {
        "type": "chips",
        "options": [
          { "text": "Under 18" },
          { "text": "18–25 years" },
          { "text": "26–35 years" },
          { "text": "36–45 years" },
          { "text": "46–60 years" },
          { "text": "Over 60 years" }
        ]
      }
    ]
  ]
}
Supplement Preview Payload
json
{
  "richContent": [
    [
      {
        "type": "info",
        "title": "SUP001 - Protein",
        "subtitle": "Supports muscle repair and satiety."
      },
      {
        "type": "info",
        "title": "SUP002 - Omega-3",
        "subtitle": "Promotes heart health and reduces inflammation."
      },
      {
        "type": "chips",
        "options": [
          { "text": "Add to Plan" },
          { "text": "More Info" },
          { "text": "Back to Menu" }
        ]
      }
    ]
  ]
}
```


## Live Chatbot Link
https://gemini.google.com/share/6f1405ad102b
