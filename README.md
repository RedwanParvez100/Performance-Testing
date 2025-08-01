# Performance Testing of a Booking Website (Test Environment)

## Introduction
This document outlines how to perform a performance test using Apache JMeter on a booking website. The goal of the test is to evaluate the website’s behavior and stability under different levels of user load.

 # Load testing Report
 
| Concurrent Request  | Loop Count | Avg TPS for Total Samples  | Error Rate | Total Concurrent API request |
|               :---: |      :---: |                      :---: |                        :---: |      :---: |
| 1  | 1  | 11.67   | 0.00%     | 100   |
| 2  | 1  |  35     | 0.00%      | 300   |
| 3  | 1  |  58.33    | 0.00%   | 500   |


## Install

### Prerequisites

Before running the performance test, ensure you have the following prerequisites installed:

- **Java**: [Download Java](https://www.oracle.com/java/technologies/downloads/)
- **JMeter**: [Download JMeter](https://jmeter.apache.org/download_jmeter.cgi) (Select the binary distribution)

### BlazeMeter (Optional)

We can also use BlazeMeter to generate JMX files for our performance tests. [BlazeMeter Chrome Extension](https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en)

## Test Plan

Create a test plan with the following elements:

- Thread Group: Simulates concurrent users.
- HTTP Request Defaults (Configuration Element): Set default values for HTTP requests.
- HTTP Request (Sampler): Define the HTTP requests to be executed.
- Summary Report (Listener): Collect and display test results.

## Collection of API

To perform the performance test, you'll need to collect the APIs from the Booking  Website.
Booking  Website Link:- https://restful-booker.herokuapp.com/apidoc/index.html
Here is a list of APIs you can use for testing:

## API Endpoints

- [POST] [`/auth`](https://restful-booker.herokuapp.com/auth) – Create auth token
- [GET] [`/booking`](https://restful-booker.herokuapp.com/booking) – Get all booking IDs
- [GET] [`/booking/:id`](https://restful-booker.herokuapp.com/booking/1) – Get booking details by ID
- [POST] [`/booking`](https://restful-booker.herokuapp.com/booking) – Create a new booking
- [PUT] [`/booking/:id`](https://restful-booker.herokuapp.com/booking/1) – Update booking details (full update)
- [PATCH] [`/booking/:id`](https://restful-booker.herokuapp.com/booking/1) – Partially update booking details
- [DELETE] [`/booking/:id`](https://restful-booker.herokuapp.com/booking/1) – Delete booking by ID


## Test Execution

Follow these steps to execute the performance test:

1. **Load the JMeter Script:**
   - File > Open (CTRL + O)
   - Locate the appropriate JMX file for your test scenario (e.g., `Booking-Website.jmx`).
   - Open the JMX file.
   - The Test Plan will be loaded.

2. **Run the Test:**
   - In the JMeter terminal, navigate to the `bin` folder.
   -  Open Command prompt (CMD).
   -  `jmeter -n -t file_name.jmx -l report\file_name.jtl` (e.g., `jmeter -n -t Booking-Website.jmx -l report\Booking-Website.jtl`)
   
   - Repeat the above command for different test scenarios as needed.

3. **Generate HTML Report:**
   - Execute the following command to generate an HTML report :
     ```bash
     jmeter -g report\file_name.jtl -o report\file_name.html 
     ```
     (e.g., `jmeter -g report\Booking-Website.jtl -o report\Booking-Website.html`)
     
   - This will create an HTML report in the `Report` folder.


  ### Summary

I’ve completed a performance test on frequently used API for test App. 
Test executed for the below-mentioned scenario.

- 100 Concurrent Request with 1 Loop Count; TTPS for Total Samples is ~ 11.667 And Total Concurrent API requested: 700.
- 300 Concurrent Request with 1 Loop Count; TTPS for Total Samples is ~ 20.0 And Total Concurrent API requested: 2100.
- 500 Concurrent Request with 1 Loop Count; TTPS for Total Samples is ~ 48 And Total Concurrent API requested: 3500.

 ## HTML Reports         |  Errors
:-------------------------:|:-------------------------:

 100 Concurrent Requests with 700 samples (APDEX, Requests Summary & Statistics Result).
 
 ![1](https://github.com/RedwanParvez100/Performance-Testing/blob/main/Report%20Images/APDEX%2C%20Requests%20Summary%20%26%20Statistics(100samples).png)

 300 Concurrent Requests with 2100 samples (APDEX, Requests Summary & Statistics Result).
 
 ![2](https://github.com/RedwanParvez100/Performance-Testing/blob/main/Report%20Images/APDEX%2C%20Requests%20Summary%20%26%20Statistics(300samples).png)

 500 Concurrent Requests with 3500 samples (APDEX, Requests Summary & Statistics Result).
 
 ![3](https://github.com/RedwanParvez100/Performance-Testing/blob/main/Report%20Images/APDEX%2C%20Requests%20Summary%20%26%20Statistics(500samples).png)


