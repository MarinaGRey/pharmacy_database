# Pharmacy Database System

This project implements a database system for managing pharmacy operations such as medication stock, employee shifts, supplier management, and orders. The system is based on a relational database schema with primary keys, foreign keys, constraints, and triggers to automate certain processes.

This project was made in collaboration with [mariamagro](https://github.com/mariamagro) for the Databases subject in the Carlos III university.

## Table of Contents
- [Introduction](#introduction)
- [Database Schema](#database-schema)
- [Constraints](#constraints)
- [Triggers](#triggers)
- [Queries](#queries)

## Introduction
This database system is designed for a pharmacy and includes tables for medications, employees, pharmacies, laboratories, suppliers, and orders. The system includes predefined constraints and triggers to ensure data integrity and automate stock replenishment processes.

## Database Schema
The database consists of the following tables:

1. **Pharmacy**: Stores information about each pharmacy, including `code`, `name`, `address`, and `schedule`.
2. **Pharmacy Phone**: Stores multiple phone numbers associated with pharmacies.
3. **Laboratory Phone**: Stores multiple phone numbers for each laboratory.
4. **Employee**: Manages employees working at the pharmacy, including `dni`, `name`, `ssn`, and `shift`.
5. **Shift & Schedule**: Stores the work shifts and schedules.
6. **Medicine**: Contains details about medications, including `code`, `lab_name`, and `type_excipient`.
7. **Type Administration & Type Excipient**: Defines how medications are administered and the types of excipients they contain.
8. **Stock**: Tracks the stock levels of medicines in pharmacies.
9. **Order**: Stores details of orders placed by pharmacies to distributors.
10. **Active Ingredients**: Stores active ingredients used in medicines.
11. **Catalogue & Product**: Stores products and their details, such as `name`, `category`, and `distributor_name`.

## Constraints
Several constraints are implemented to maintain the integrity of the database:
- **Primary Keys (PK)**: Ensure that each record in a table is unique. For example, `pharmacy_code` is the primary key in the `pharmacy` table.
- **Unique Constraints**: Ensure certain fields, such as `dni` in the `employee` table, are unique.
- **Check Constraints**: Validate data inputs. For instance, `type_administration` can only be `'Orally'` or `'Intravenous'`, and `type_excipient` can only be one of `'Capsule'`, `'Tablet'`, `'Pill'`, `'Cream'`, `'Spray'`, or `'Syrup'`.

## Triggers
The following triggers automate database operations:
1. **Trigger to Automatically Assign Sequence IDs**: For example, a trigger is set to auto-increment the `code` in the `medicine` and `type_administration` tables using sequences.
   - Example: `tg_codemedicine` auto-generates `medicine.code`.
   
2. **Trigger for Automatic Order Creation**: When the stock of any medicine drops below 3 units, a new order is automatically created to restock 50 units from a distributor.
   - Example: `lab_tg1_stock_aiu` checks stock levels and places an order when necessary.

## Queries
Predefined SQL queries are available to extract and manipulate data:
1. **Average Number of Medications per Pharmacy**
2. **Employees Working the Day Shift**
3. **Number of Orders by Pharmacy**
4. **Number of Orders Between May and June 2022**
