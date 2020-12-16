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

### ![Click Here for Full Data Dictionary](https://github.com/aharabedian/database_project/blob/main/data_dictionary.pdf)

## ![SQL Dump Script](https://github.com/aharabedian/database_project/blob/main/Updated_Campus_Eats_Data_Dump.sql)

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
