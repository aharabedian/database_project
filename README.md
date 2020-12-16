# 3160 Database Project

## Introduction

The goal of this project is to extend the CraveOnCampus database by adding a driver and resturant rating system. This project extends the database that was designed by a previous team in the ITSC3160 course, only the rating system is original work. The rating system additions include a use case diagram, business rules, ERD, and data dictionary. The changes will be documented in this GitHub readme.

## Team Members
This is a solo project by **Aaron Harabedian** <aharabed@uncc.edu>

## Use Case
![Use Case Image](https://github.com/aharabedian/database_project/blob/main/ITSC%203160%20Use%20Case.png)

## Business Rules
* Customers can leave ratings for every order.

*	Every rating will allow a driver rating and a resturant rating and a comment.

*	Customers can view the ratings for a driver and resturant.
	
*	Customers can view their ratings by their orders.
	
*	Administrators can view ratings by order.

*	Only one rating can be attached to one order.

*	The ratings will be out of five

*	Administrators can view and delete ratings.

## ERD
![ERD Image](https://github.com/aharabedian/database_project/blob/main/ERD.png)

## Data Dictionary for New Tables

### Table: rating
|       Name      |   Data Type  | Nullable |  PK |  FK | Default |
|:---------------:|:------------:|:--------:|:---:|:---:|:-------:|
| rating_id       | INT(11)      | Yes      | Yes | No  |         |
| resturant_score | TINYINT      | No       | No  | No  | NULL    |
| driver_score    | TINYINT      | No       | No  | No  | NULL    |
| comment         | VARCHAR(255) | No       | No  | No  | NULL    |
| order_id        | INT(11)      | Yes      | No  | Yes |         |
| restaurant_id   | INT(11)      | Yes      | No  | Yes |         |
| driver_id       | INT(11)      | Yes      | No  | Yes |         |

### [Click Here for Full Data Dictionary](https://github.com/aharabedian/database_project/blob/main/data_dictionary.pdf)

### Select Ratings Table

![Select Ratings Table](https://github.com/aharabedian/database_project/blob/main/SelectRating.png)

## [SQL Dump Script](https://github.com/aharabedian/database_project/blob/main/Updated_Campus_Eats_Data_Dump.sql)

## Stored Procedures

### Calculate Resturant Ratings
This procedure calculates the average rating for each resturant and displays it with the resturant in descending order.

![Calculate Resturant Ratings](https://github.com/aharabedian/database_project/blob/main/RRating.png)

### Calculate Driver Ratings
This procedure calculates the average rating for each driver. It displays the rating as well as the driver's name and contact information if it can be pulled from the associated person.

![Calculate Driver Ratings](https://github.com/aharabedian/database_project/blob/main/DRating.png)

### Add Rating
This procedure adds a rating to an order. It takes the order ID and uses it to look up the fields required to link a rating to the driver and restaurant.

![Add Rating](https://github.com/aharabedian/database_project/blob/main/AddRating.png)

## Custom Views

### Bad Orders
This view shows all orders with a driver or restaurant score below 3.0. It includes the order price, restaurant and driver scores and restaurant and driver names. This view can be used to find consistendly underperforming drivers or restaurants. It is sorted by driver score as this is what can be most easily fixed.

![Bad Orders](https://github.com/aharabedian/database_project/blob/main/BadOrders.png)

### Good Orders
This view shows all orders with a driver and restaurant score above 3.0. It includes the order price, restaurant and driver scores and restaurant and driver names. This view can be used to find restaurants and drivers that consisntently provide good experiences to customers.

![Good Orders](https://github.com/aharabedian/database_project/blob/main/GoodOrders.png)

## Indexes and Explain

## Explain ratings table

![Explain ratings](https://github.com/aharabedian/database_project/blob/main/ExplainRatings.png)

This implementation of the ratings table uses foreign keys for the order id, restaurant id, and driver id. These allow for flexible usage of the ratings table and for complex relationships to exist between restaruants, ratings, orders, and drivers. If a driver or restaurant is removed, the ratings will stay attached to the order. This allows for a better historical record of rating data. This also allows for optimized queries because ratings can be linked directly to drivers or restaurants. This makes getting ratings for restaurants simple and less expensive because no joins need to be performed. This also allows old order data to be purged while retaining the ratings associated with that order. We believe that this rating implementation creates a flexible system at the cost of a few redundant data points.

## [Presentation Video](https://youtu.be/hI8hiGJRmmI)
[PowerPoint Download](https://github.com/aharabedian/database_project/raw/main/3160%20Database%20Project.pptx)
