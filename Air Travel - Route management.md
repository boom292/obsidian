## Use cases

### Add Airports / Routes

- **Actors**: Airport Authorities, Airlines
- **Description**: This allows for the addition of new airports and routes to the system, enabling better connectivity and expansion of air travel networks.
- Detailed Description: Airports and routes are added based on demand, geographical importance, and regulatory approvals to ensure efficient air travel management.

### Airline slot allocation

- **Actors**: Government, Airlines
- **Description**: This allows for the airlines to reserve slots at airports to use for arrivals and departure.
- Detailed Description: A slot is very important to airlines, since the more slots they have the more they can profit from that airport. A slot is given to an airline based on a lot of factors, such as aircraft type, turnaround time and parking duration.

### Airline route allocation

- **Actors**: Government of countries, Airlines
- **Description**: This allows for countries to give a route that involves more than one country to an airline. This is important because airlines generate international brand value through international flights.
- Detailed Description: This type of agreement requires some form of regulation in terms of which airline can fly a certain number of flights in a week.

## Tables
```bash
├── Airports
│ └── Slots ( Reserved by )
├── Routes
│ └── Reserved-by
├── Airlines
├── Treaties ( Agreements between countries )
├── Countries ( Is this needed? )
```
### Tables Description
#### Airports

| Field              | Description                                |
| ------------------ | ------------------------------------------ |
| ID                 | Unique identifier for the airport          |
| Name               | Full name of the airport                   |
| Location           | City and country of the airport            |
| PassengerTerminals | Number or list of terminals for passengers |
|CargoTerminals | Number or list of terminals for cargo
|Capacity | Max flights or passengers the airport can handle per day

#### Slots

| Field | Description            |
| ----- | ---------------------- |
| ID    | Unique slot identifier |
|AirportID | Foreign key referencing Airports
|AirlineID | Foreign key referencing Airlines
|TimeWindow | Time slot allocated (e.g., 08:00–08:30)
|TurnaroundTime | Time needed to prep the aircraft for next flight
|ParkingDuration | Duration the aircraft stays at the airport
|Season | Season for which the slot is valid (e.g., Summer 2025)

#### Routes

| Field | Description |
| --- | --- |
|ID | Unique route identifier
|FromAirportID | Departure airport (foreign key to Airports)
|ToAirportID | Destination airport (foreign key)
|Distance | Distance between airports (in km or miles)
|ReservedBy | Airline(s) who operate on this route
|TreatyID | If international, links to a Treaty

#### Airlines

| Field | Description |
| --- | --- |
|ID | Unique airline identifier
|Name | Official name of the airline
|CountryID | Foreign key to the airline’s country of origin
|FleetSize | Number of aircraft in oField | Descriptionperation
|InternationalCarrier | Whether the airline has international rights (boolean)

#### Treaties

| Field | Description |
| --- | --- |
|ID | Unique treaty identifier
|CountryAID | First country involved
|CountryBID | Second country involved
|AllowedFlightsPerWeek | Max flights allowed between the two countries per week
|ValidFrom | Start date of the treaty
|ValidUntil | End/review date of the treaty
|Notes | Additional details or special clauses

#### Countries

| Field | Description |
| --- | --- |
|ID | Unique country identifier
|Name | Official name of the country
|ICAOCode | ICAO country code
|AirspaceCapacity | Optional: flight volume capacity of national airspace
