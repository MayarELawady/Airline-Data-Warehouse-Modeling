# Airline-Data-Warehouse-Modeling
Analyze a major airline company's current business processes and expanding the company by discovering new opportunities by Analyzing flight activities,
reservation process and customer care interaction.

## Applied using Bill Inmon data model, ERD- Dimensional Modeling (snowflake schema)

## The Grain:
Flights per segment (Transit).
Segment is the stop point for each flight if it’s not a one way flight

## Dimensions:
Passenger, Flight, Promotion, Flight_Status, Resv_Channel, Feedback, Feedback type,
Class_type, FareBasis, Airport

## Facts:
- Flight_activity: Total_miles, Segment_Duration,ticket fees.
- Promotions_respose: Factless table(Passenger_key, Promotion_key, Flight_key)
- Class Upgrades: Factless table(Class_key, Passenger_key, Flight_key)
- Passenger_Interactions: Total complaint, Total feedbacks, total inquires.


## Assumptions:
- To be a frequent flier you must exceed 6000 miles, (the total miles for that passenger
flight)
- Passengers often Upgrade, Downgrade or don’t change their class type for the flight
11
- Passengers is a (Slowly Changed Dimension) to change the passenger_flight_status when
they earn a certain total amount of miles.
If total mile more than 5000 and less than 10000 then he will have titanium status
else if total mile more than 10000 and less than 5000 he will be upgraded to platinum,
Else if he exceeded 10000 miles he will have a gold status.
- When Receiving feedbacks from passengers, it’s divided into 3 categories,
either it’s a problem, inquiry or a feedback, and if it’s a problem it will have an indicator
problem severity, which have a rate from 1 to 10 to indicate how severe is that problem
