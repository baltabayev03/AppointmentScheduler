# Appointment scheduler

>This is a Spring Boot Web Application to manage and schedule appointments between providers and customers. It has many features such as automatic invoicing, email notifications, appointments cancelation, providers individual working plans with brakes etc.


<a href="https://github.com/baltabayev03/margulan-github.io/blob/main/image.png?raw=true"><img src="https://github.com/baltabayev03/margulan-github.io/blob/main/image.png?raw=true" width="600"></a>

| Account type | Username | Password 
| --- | --- | --- |
| `admin` | admin | qwerty123 |
| `provider` | provider |qwerty123 |
| `corporate customer` | customer_c |qwerty123 |
| `retail customer` | customer_r |qwerty123 |


## Account types 

`admin` -  is created at database initialization. Admin can add new providers,  services and assign services to providers. Admin can see list of all: appointments, providers, customers, invoices. He can also issue invoices manually for all confirmed appointments.

`provider` - can by created by admin only. Provider can set his own working plan, add brakes to that working plan and change his available services. Provider sees only his own appointments.

`customer retail` - registration page is public and can be created by everyone. Customer can only book new appointments and manage them. This type of customer sees only services which targets retail customer.

`customer corporate` - almost the same as retail customer. The only difference is that this type of account needs to provide VAT number and Company Name and can see only services which targets corporrate customer.

## Booking process

To book a new appointment customer needs to click `New Appointment` button on all appointments page and then:

1. Choose desired work from available works list
2. Choose provider for selected work
3. Choose on of available date which is presented to him
4. Click book on confirmation page

Available hours are calculatated with getAvailableHours function from AppointmentService:

`List<TimePeroid> getAvailableHours(int providerId,int customerId, int workId, LocalDate date)`

This function works as follow:

1. gets selected provider working plan
2. gets working hours from working plan for selected day 
3. excludes all brakes from working hours
4. excludes all providers booked appointments for that day
5. excludes all customers booked appointments for that day
6. gets selected work duration and calculate available time peroids 
7. returns available hours


