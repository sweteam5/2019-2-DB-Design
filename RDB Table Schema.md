# ERD Table Schema

## Before Redundancy
### Entities
* Customer ( **ID**, name, phone_number, point )
* Movie ( **ID**, title, opening_day, running_time )
* ScreenInfo ( **ID**, start_time )
* Branch ( **ID**, branch_name, address, tel )
* Theater ( ***Branch.ID*, ID**,  name, capacity, price )
* SeatInfo ( ***Branch.ID*, *Theater.ID*, ID**, name ) 
* Worker ( **ID**, name, position, salary, phone_number )
* Reservation ( **resNum** )
* Ticket ( ***resNum*, ticketNum** )
* Seat_Type ( **type**, weight )

### Relationships
* Movie_Review ( ***Customer.ID***, ***Movie.ID***, rating, content )
* Theater_Review ( ***Customer.ID***, ***(Branch.ID, Theater.ID)***, rating, content )
* Movie_Schedule ( ***Movie.ID***, ***ScreenInfo.ID*** )
* Theater_Schedule ( ***(Branch.ID, Theater.ID)***, ***ScreenInfo.ID*** )
* Customer-Reservation ( ***Customer.ID***, ***Reservation.ID*** )
* ScreenInfo-Reservation ( ***ScreenInfo.ID***, ***Reservation.ID*** )
* ScreenInfo-Theater ( ***ScreenInfo.ID***, ***(Branch.ID, Theater.ID)*** )
* ScreenInfo-SeatInfo ( ***ScrennInfo.ID***, ***(Branch.ID, Theater.ID, SeatInfo.ID)*** )
* Ticket-Seat ( ***(resNum, ticketNum)***, ***(Branch.ID, Theater.ID, SeatInfo.ID)*** )
* Worker - Branch ( ***Worker.ID***, ***Branch.ID*** )
* Ticket - SeatType ( ***Ticket.type***, ***Seat_Type.type*** )

## After Redundancy
* Customer ( *ID*, name, phone_number, point )
* Movie ( *ID*, title, opening_day, running_time )
* ScreenInfo ( *ID*, start_time, Movie.ID*, *(Branch.ID, Theater.ID)* )
* Branch ( *ID*, branch_name, address, tel )
* Theater ( ***Branch.ID*, ID**,  name, capacity, price )
* SeatInfo ( ***Branch.ID*, *Theater.ID*, ID**, name, *ScreenInfo.ID* )
* Worker ( **ID**, name, position, salary, phone_number, *Branch.ID* )
* Reservation ( **resNum**, *Customer.ID*, *ScreenInfo.ID* )
* Ticket ( ***resNum*, ticketNum**, *type*, *(Branch.ID, Teather.ID, SeatInfo.ID)* )
* Seat_Type ( **type**, weight )
* Movie_Review ( ***Customer.ID***, ***Movie.ID***, rating, content )
* Theater_Review ( ***Customer.ID***, **(*Branch.ID*, *Theater.ID*)**, rating, content )
