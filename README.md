AirBnB-API API Controller
This repository contains a RESTful API implemented in Java using Spring Boot for managing listing information. The API provides endpoints for CRUD operations (Create, Read, Update, Delete) along with additional functionalities such as PATCH, HEAD, and OPTIONS requests.

Endpoints
GET /api/listings
Retrieves a list of all listings.

GET /api/listings/{listingId}
Retrieves details of a specific listing by ID.

POST /api/listings
Adds a new listing. Requires a JSON payload with listing details.

PUT /api/listings/{listingId}
Updates an existing listing's details. Requires a JSON payload with updated listing information.

DELETE /api/listings/{listingId}
Deletes a listing by ID.

PATCH /api/listings/{listingId}
Partially updates a listing's details based on provided fields in the request body.

HEAD /api/listings/{listingId}
Checks for the existence of a listing by ID without fetching the full resource.

OPTIONS /api/listings/{listingId}
Retrieves the HTTP methods supported for a listing resource.

Error Handling
The API returns appropriate HTTP status codes and messages, including 404 Not Found for resources that do not exist.
Input validation is handled using Jakarta Bean Validation (@Valid annotation) for request bodies.

Technologies Used
Spring Framework: For dependency injection and MVC architecture.
Jakarta Bean Validation: For validating input data.
Postman: For unit testing.

Usage
To use this API, ensure you have Java and Maven installed. Clone the repository, build the project using Maven, and deploy it to your preferred application server.


HERE IS HOW YOU CAN CREATE YOUR OWN API THAT IS JUST LIKE THIS 

Set up the Spring Boot project:
Create a new Spring Boot project using the Spring Initializer.
Choose dependencies such as Spring Web, Spring Data JPA, Spring Validation, and a database driver (e.g., MySQL driver).

Create the Entity class:
Create a Listing class that represents the listing data.
Add fields such as id, host_first_name, host_last_name, host_email, title, description, price, location, etc.
Annotate the class with JPA annotations (@Entity, @Table, @Id, @GeneratedValue, etc.) to map it to a database table.
Add validation annotations, such as @NotBlank, @Email, @Min, and @Max, to ensure data integrity.

Create the Repository Interface:
Create a ListingRepository interface that extends JpaRepository<Listing, Integer> or any other appropriate data type for the id field.
This interface will provide the basic CRUD (Create, Read, Update, Delete) operations for the Listing entity class.

Implement the Listing Service:
Create a ListingService class and annotate it with @Service.
Inject the ListingRepository into the service class.
Implement the necessary methods for CRUD operations, such as getAllListings(), getListingById(int id), createListing(Listing listing), updateListing(int id, Listing listing), and deleteListing(int id).

Create the Listing Controller:
Create a ListingController class and annotate it with @RestController and @RequestMapping("/api/listings").
Inject the ListingService into the controller class.
Implement the necessary REST API endpoints, such as:
`@GetMapping("/"): Get all listings
`@GetMapping("/{id}"): Get a listing by ID
`@PostMapping("/"): Create a new listing
`@PutMapping("/{id}"): Update an existing listing
`@DeleteMapping("/{id}"): Delete a listing
`@PatchMapping("/{id}"): Partially update a listing
`@RequestMapping(value = "/{id}", method = {RequestMethod.HEAD}): Head request to check the existence of a listing
`@RequestMapping(value = "/{id}", method = RequestMethod.OPTIONS): Options request to retrieve the supported HTTP methods for a listing

Handle Exceptions:
Create a GlobalExceptionHandler class and annotate it with @RestControllerAdvice.
Implement exception handling methods to handle common exceptions, such as MethodArgumentNotValidException (for validation errors) and ResponseStatusException (for custom error handling).
Provide appropriate HTTP status codes and error responses.

Configure the Application Properties:
Update the application.properties file with the necessary database connection details (URL, username, password).
