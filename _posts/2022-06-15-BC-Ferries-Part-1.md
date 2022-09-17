## BC Ferries - Part 1

![Image of ferry](/grahamwarner/images/ferry_landscape.jpg)

### Project Introduction

I live on Vancouver Island and occasionally travel from Swartz Bay to Tsawwassen via [BC Ferries](https://www.bcferries.com), usually with my car. The ferries on this route run every 1-2 hours and can get full during busy times so you might need to wait a sailing (or more) if you're unlucky. You can drive to the terminal and purchase a ticket with the hopes that there will be space available, or you can purchase a reservation ($17.00 at time of writing) to reserve your spot. You can purchase reservations up to the day before sailing, as long as the reservations haven't sold out. In order to claim your reservation, you must arrive at the terminal between 30 and 60 minutes before the scheduled sailing time. Your reservation is void if you show up less than 30 minutes before sailing.

There are 2 situations to avoid:
1. Arriving at the ferry terminal just after the ferry becomes full. This is frustrating because you may have to wait 1+ hours for the next ferry, and had you arrived slightly earlier, you might have saved yourself hours of wait time.
2. Paying for a reservation and then finding the ferry empty once you get to the terminal.

It can take several minutes to get through the ticketing lineup, so if you purchase a reservation you would likely aim to arrive at the terminal ~40 minutes before sailing (assuming <10 minutes in the lineup). 

There are two situations that I want to model for this project:
1. You are planning a trip well in advance and know you will be constrained by time so you will only be able to arrive at the terminal 40 minutes before sailing. You would like to know if your planned sailing will be full so you can decide if you need to purchase a reservation. If the sailing won't be full, there is no need to waste money on a reservation.
2. You are trying to get on a particular sailing but haven't purchased a reservation. You have flexibility in how early you can arrive at the terminal so you want to know at what time the ferry will become full. Your strategy might be to arrive at the terminal 10 minutes before the sailing becomes full to make sure you get on the ferry but don't waste excessive time waiting at the terminal.

### Data Collection and Exploration

In order to predict if or when your ferry is going to be full, we need to collect data on how often ferries are full.

