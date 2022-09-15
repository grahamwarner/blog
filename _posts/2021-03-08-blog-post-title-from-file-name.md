## Project Introduction

I live on Vancouver Island and occasionally travel from Swartz Bay to Tsawwassen via BC Ferries, usually with my car. The ferries on this route run every 1-2 hours and can get full during busy times so you might need to wait a sailing (or more!) if you're unlucky. You can drive to the terminal and purchase a ticket with the hopes that there will be space available, or you can purchase a reservation ($17.00 at time of writing) to reserve your spot. You can purchase reservations up to the day before sailing, as long as the reservations haven't sold out. In order to use your reservation, you must arrive at the terminal between 30 and 60 minutes before the scheduled sailing time.

There are 2 situations that I'd like to avoid:
1. Arriving at the ferry terminal just after the ferry becomes full. This is frustrating because you may have to wait 1+ hours for the next ferry, and had you arrived slightly earlier, you might have saved yourself hours of wait time.
2. Paying for a reservation and then finding the ferry empty once you get to the terminal.

Your reservation is void if you show up less than 30 minutes before sailing. It can take several minutes to get through the ticketing lineup, so if you purchase a reservation you would likely aim to arrive at the terminal ~40 minutes before sailing (assuming <10 minutes in the lineup). 

There are two use cases 
1. Let's say you are planning a trip well in advance and know you are constrained by time so you can only arrive at the terminal 40 minutes before sailing. You would like to know if your planned sailing will be full so you can decide if you need to purchase a reservation. If the sailing won't be full, there is no need to waste money on a reservation.
2. Let's say you haven't purchased a reservation and are trying to get on a particular sailing. You have flexibility in how early you can arrive at the terminal so you want to know at what time the ferry will become full. You might aim to arrive at the terminal 10 minutes early to make sure you get on the ferry but don't waste excessive time waiting at the terminal.

---

### This is a header

#### Some T-SQL Code

```tsql
SELECT This, [Is], A, Code, Block -- Using SSMS style syntax highlighting
    , REVERSE('abc')
FROM dbo.SomeTable s
    CROSS JOIN dbo.OtherTable o;
```

#### Some PowerShell Code

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```
