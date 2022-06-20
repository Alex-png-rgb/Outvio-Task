# Outvio-Task

In this repository there are 3 files:
- MS Word containing the task
- Power BI answering question 1
- Excel answering question 2

## Part 1

To answer the questions posed for the part one I created a Power BI dashboard that connects 3 sheets of data provided.

There are 2 pages to the dashboard:
1. First page answers the specific questions asked
 - Average delivery time per courier
 - Average delivery time per shipping method
 - Average products per order

2. Second page answers two additional questions:
  - Total product cost per package per courier
  - Product weight and total package weight per courier

#### Dependencies

The dashboard requires Power BI desktop version: 2.106.582.0

## Part 2

To answer the second question using Excel I first calculated average number of orders using ARPU and the costs provided using the provided equation: 

`
ARPU = subscription fee + (order fee x average number of orders processed)
`

Then I split module costs in two parts 'fee per order' and 'module fee'. Based on new variables I created the following equation for all 3 segments: 

`
ARPU = subscription fee + module_usage_%_1*module_subcription_fee_1 + ... + module_usage_%_n*module_subcription_fee_n + average number of orders processed*(order fee + module_usage_%_1*module_order_fee_1 + ... + module_usage_%_n*module_order_fee_n), where n=4
`

Here 
  - module_usage_%_1 represents percentage of clients in that plan that are using the functionality included in module 1
  - module_subcription_fee_1 represents fee a client pays to subscribe to the functionalies included in module 1
  - and module_order_fee_1 represents an additional fee per order for clients utilizing functionalities from module 1


I have set up a solver function in Excel to have certain constraints:
1. Subscription fee has to be lower than before to lower the entry barrier
2. Fee per order has to be lower than before to lower the entry barrier
3. Modular fees per order have to be lower than general fee per order
4. Module fee need to reflect their popularity



I solved this as a linear function for the Conquer segment - as this is the segment that generates most income. The goal of the function was to make new ARPU values be close to the existing ARPU by changing the unkown variable values.

I then copied the modular fees and modular fees per order to other segments and reduced subscription fee so that ARPU stays the same. Thus 
lowering subscription fees and fees per order, reducing the entry barrier but keeping the pofitability at maximum.

NB in my model Desk Support doesn't come at additional price.
