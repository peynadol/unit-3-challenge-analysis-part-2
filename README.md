# Unit 3 Challenge - Analysis Part 2

### Todos
- [x] Initial read through of spec and wireframes/ all supporting docs
- [x] Work through the spec and wireframes, analyse requirements, think about **what** I can test
- [x] Make notes on anything i think is important e.g. test areas, risks, assumptions and questions
- [x] Draw diagrams if they’ll help
- [x] List the parts of the project i want to focus in on during a first 90 min exploration session. Prioritise. 
- [x] Write down **how** i might test those parts of the project - include test cases, steps, test data etc
- [X] Commit resources to GH

## Project Spec - MakersBnB
Web app that allows users to list spaces they have available, and to hire spaces for the night.

### Headline Specifications
- Any signed up user can list a new space
- Users can list multiple spaces
- Users should be able to name their space, provide a short desc of the space, and a price per night
- Users should be able to offer a range of dates where their space is available
- Any signed up user can request tohire any space for one night, and this should be approved by the user that owns that space
- Nights for which a space has already been booked should not be available for users to book that space
- Until a user has confirmed a booking request, that space can still be booked for that night

### Nice to haves
- Users should receive an email whenever one of the following happens:
  - They sign up
  - They create s space
  - They update a space
  - A user request to book their space
  - They confirm a request
  - They request to book a space
  - Their request to book a space is confirmed
  - Their request to book a space is denied
- Users should receive a text message to a provided number whenever one of the following happens:
  - A user request to book their space
  - Their request to book a space is confirmed
  - Their request to book a space is denied
- A ‘chat’ functionality once a space has been booked, allowing users whose space booking request has been confirmed to chat with the user that owns that space
- Basic payment implementation through Stripe


### Initial thoughts - scratchpad

- the two request pages appear to share the same url - are these the same page with two separate states of two separate pages? How does the user navigate from the requests list (showing both ones made and received) to just a received
- How is money changing hands if payment is a ‘nice to have’?
- Booking logic can be complex - need to think about not overbooking and available dates
  - If a user is due to leave in the AM on a Friday, will the app show that as available for another user? Will they be told its free after x o clock?

### Homepage
- Logo should be visible top left
- Sign up form is visible on the home page with fields for:
  - email
  - password
  - password confirmation
- Sign up button should be visible and functional
- ’Feel at home, anywhere’ and blurb text should be visible
- Text ‘Sign up to MakersBnB’ above form
- email field should only accept valid emails
- passwords should be valid
- password and password confirmation field MUST match
- valid and invalid inputs should be tested across all fields
- ’about’ and ‘login’ link visible top right
- the login link should navigat you to the login page
- any site functionality beyond homepage should not be accessible without being logged in
- are informing users if they already have an account if they do and try to sign up?
- what’s the plans for the about page? can’t see one in mockup
- do we have password requirements?

### Log in page
- Login form is visible on the homepage with fields for:
  - email address
  - password
- Log in button should be visible and functional
- ’Log in to MakersBnB’ text should be visible above form box
- Logo should be visible top left
- ’about’ and ‘login’ link visible top right
- Login should ‘redirect’ you to the login page even if you’re already on it
- If account credentials are correct - user should be logged in
- If account credentials are incorrect - inform user - be wary of how much information we give
- If a user ends up on the login page mistakenly, how are they to get to the sign up/ homepage? Is there a link? A hint?
- What happens if there’s repeated failed login attempts?
- Once logged in, where are we redirecting the user?

### Spaces page
- Logo should be visible top left
- ’Spaces’, ‘Requests’, and ‘Sign out’ links should be visible top right
- ’Book a Space’ text and blurb underneath it should be visible
- List a space button should be visible and functional - sending user to the ‘New Space page’
- Available from and Available to date pickers should be functioning
- Date in picker format should match label text (DD/MM/YY)
- The ‘List Spaces’ button should be visible and functional
- When the user has entered dates, and presses the ‘List Spaces’ button, a list of available spaces should render in a list 
- What happens if the user clicks the ‘List Spaces’ button with no dates entered?
- What happens if the users clicks the ‘List Spaces’ button with only one date picked? Either from or to.
- Clicking on one of the spaces rendered in a list should take the user to the ‘Space page’ 
- What happens in the user picks a ‘from’ date after the ‘to’ date?
- Will the date picker ‘grey out’ all dates before the current date?

### List a Space page
- Logo should be visible top left
- ’Spaces’, ‘Requests’, and ‘Sign out’ links should be visible top right
- Clicking the ‘Requests’ link should take the user to the ‘Requests page’ 
- ’List a Space’ text and blurb underneath it should be visible
- The user should see a form containing the following fields:
  - Name
  - Description
  - Price per night (£)
  - Available from (DD/MM/YY)
  - Available to (DD/MM/YY)
- Date in picker format should match label text (DD/MM/YY)
- The ‘List my Space’ button should be visible and functional
- When a user lists a space, they are redirected to the ‘Spaces page’, but on the wireframe I interpret the ‘Spaces page’ as a place to view Spaces from the perspective of a potentially dweller, not a space owner. Should we have a ‘My Spaces’ page specifically for spaces we’ve listed?
- If the user has multiple spaces to list, is redirecting them on click of the button nice UX? 
- What happens in the user picks a ‘from’ date after the ‘to’ date?
- Will the date picker ‘grey out’ all dates before the current date?
- Is there a character limit on the Name field?
- Is there a caracter limit on the Description field?
- Are we cencosring/ filtering certain words?
- How are we validating the Price per Night field? Can the user enter negative numbers? 

### Space page
- Logo should be visible top left
- ’Spaces’, ‘Requests’, and ‘Sign out’ links should be visible top right
- Clicking ‘Spaces’ link should take the user to the ‘Spaces page’ 
- The text of the name of the space should be visible
- Extra text should be visible underneath the name of the space, will this be the description?
- The user should be able to see a date picker:
  - Available dates should be clickable
  - Non available dates should be greyed out and not clickable
- There should be a visible and functional ‘Request to Book’ button
- What happens if the user presses this without selecting a date? Are we disabling the button until the user has selected a date?
- Once the user has selected a valid date, and pressed the booking button, what is their flow? Are they being redirected to another page? I know we have email in the nice to have, but other than that - how are we making their experience/ interaction nice?
- I can see a user can go into the ‘Requests’ page to see their booking requests, should be make that clearer to them? Or redirect to that page on booking button press?
- Can a user book their own space? Need clarity on whether our application allows that or not. There may be cases where the user wants to do that. 

### Requests page
- Logo should be visible top left
- ’Spaces’, ‘Requests’, and ‘Sign out’ links should be visible top right
- The text ‘Requests’ should be visible
- The user should be able to see two columns:
  - Requests I’ve made
    - Clicking a space in this column should redirect the user to the ’Spaces page’, at the specific space 
  - Requests I’ve received
    - I don’t see a page for confirmation pages on the wireframe. Is this a future feature?
- In each column, the applicable spaces should be listed
- What happens if there’s no requests at all, are we rendering a nice user message?
- How does a user confirm a booking request?

### Request page
- Logo should be visible top left
- ’Spaces’, ‘Requests’, and ‘Sign out’ links should be visible top right
- The text ‘Request for [space name]’ should be visible
- The user should be able to see details about the user who has made the request:
  - Is the date to, or from?
  - Not enough information on duration
- The user should see a list of ‘other requests’ for this same space:
  - Is this a queue?
    - Sticky note on wireframe confirms it’s a queue
    - Sticky note on wireframe confirms that other requests for a Space on that night are auto denied
- How does a user get into this page? Wireframe doesn’t make it clear
- The wireframe from this page, and the Requests (plural) page have the same URL, is this correct?
- Is there security in place so this URL isn’t accessible by any other user?

### Diagrams
Booking States
<img width="619" height="511" alt="image" src="https://github.com/user-attachments/assets/d9e9ad19-4dd2-4b66-b252-380421165538" />

  

## 90 minute exploratory test focus

Due to time contraints, this session will not focus on any of the ‘Nice to haves’. These can be prioritised for a future session once core functionality is tested and verified.

Two things immediately come to my mind in regards to importance. They are security/ authentication and the Booking logic. 

Security and Auth because if this is failing then nothing else matters. Ensure users can log in correctly, that accounts are protected, and certain pages are inaccessible unless logged in.

Booking Logic because this is vital for the user. It’s the core purpose of the application, to send and receive bookings. If this fails, or part fails, it’ll impact customers and the business.

This means i’d likely split my 90 minutes over these two topics/ focusses. I may be wrong, but i’ve a feeling that the Booking logic will be more complex and have more test cases to cover. With this in mind, I’d split the time to:
- 30 minutes on Auth
- 60 minutes on Booking logic

## Auth Test Cases

### Test Case: Successful Login
**Steps**:
1. Navigate to http://makersbnb.herokuapp.com
2. Click the Login link in the top right
3. Enter a valid email into the email field
4. Enter the correct password into the password field
5. Click the login button

**Test Data**:
- Email: exampleuser@example.com
- Password: Password123

**Expected Result**:
User is logged in and redirected to the appropriate page

### Test Case: Failed Login
**Steps**:
1. Navigate to http://makersbnb.herokuapp.com
2. Click the Login link in the top right
3. Enter a valid email into the email field
4. Enter the incorrect password into the password field
5. Click the login button

**Test Data**:
- Email: exampleuser@example.com
- Password: WrongPassword123

**Expected Result**:
User to not be logged and should be shown an appropriate error message. Exactly wording and behaviour not specificed.


### Test Case: Accessing a protected page without being logged in
**Steps:**
1. Ensure user is not logged in
2. Navigate to http://makersbnb.herokuapp.com/spaces/new

**Expected Result**:
Non logged in user should be redirected to login page when trying to access a protected page. This is assumed behaviour, not specificed in spec.


### Test Case: Successful sign up
**Steps:**
1. Navigate to http://makersbnb.herokuapp.com
2. Enter a valid, non registered email into the email field
3. Enter a valid password into the password field
4. Enter the same password into the password confirmation field
5. Click sign up

**Test Data**:
- Email: newuser@example.com
- Password: Password123
- Password Confirmation: Password123

**Expected result**:
Account is created and user is redirected to appropriate page

### Test Case: Failed signup (mismatched passwords)
**Steps**:
1. Navigate to http://makersbnb.herokuapp.com
2. Enter a valid, non registered email into the email field
3. Enter a valid password into the password field
4. Enter a different password into the password confirmation field
5. Click sign up

**Test Data**:
- Email: newuser1@example.com
- Password: Password123
- Password: DifferentPassword123

**Expected result**:
Account is not created and user is shown an appropriate error message

### Test Case: Sign out and attempt to access protected page
**Steps**:
1. Login with valid credentials
2. Click sign out
3. Click the browser back button
4. Attempt to navigate diretly to http://makersbnb.herokuapp.com/spaces/new

**Test Data**:
- Email: exampleuser@example.com
- Password: Password123

**Expected Result**:
Non logged in user should be redirected to login page when trying to access a protected page. This is assumed behaviour, not specificed in spec.

## Booking Logic Test Cases

### Test Case: Successfully request a space for an available date
**Steps**:
1. Log in with valid credentials
2. Navigate to the spaces page - http://makersbnb.herokuapp.com/spaces
3. Enter a valid date range and click List Spaces
4. Click on an available space - this should redirect to a Space page - such as http://makersbnb.herokuapp.com/spaces/1
5. Select an available date on the date picker
6. Click request to book

**Test Data**:
- Email: requester@example.com
- Password: Password123
- Date: A date within the space’s available range

**Expected Result**:
Booking request is created and appears in the user’s requests page as Not Confirmed

### Test Case: Owner confirms a booking request
**Steps**:
1. Log in with valid credentials
2. Navigate to the requests page - http://makersbnb.herokuapp.com/requests
3. Click on a pending request under the column ‘Requests I’ve received’ - this should redirect to a ‘Request Page’
4. Click on a pending request
5. Click confirm request

**Test Data**:
- Email: owner@example.com
- Password: Password123

**Expected result**:
Request status changes to Confirmed for both the owner and the requester

### Test Case: Owner denies a booking request
**Steps**:
1. Log in with valid credentials
2. Navigate to the requests page - http://makersbnb.herokuapp.com/requests
3. Click on a pending request under the column ‘Requests I’ve received’ - this should redirect to a ‘Request Page’
4. Click on a pending request
5. Click deny request

**Test Data**:
- Email: owner@example.com
- Password: Password123

**Expected result**:
Request status changes to Denied for both the owner and the requester. Other pending requests for the same space and date should remain as Not Confirmed.

### Test Case: Confirming one request auto denies others for the same space and date
**Steps**:
1. Log in with valid credentials
2. Ensure that there are at least two pending requests for the same space on the same date
3. Navigate to the requests page - http://makersbnb.herokuapp.com/requests
4. Click on one of the pending requests
5. Click Confirm Request

**Test Data**:
- Email: owner@example.com
- Password: Password123
- Two Requesters with pending requests for the same space and date

**Expected Result**:
The confirmed request shows as Confirmed. All other pending requests for that space on that date are automatically set to Denied.

### Test Case: Attempting to book an already confirmed date
**Steps**:
1. Log in as a user
2. Navigate to the spaces page - http://makersbnb.herokuapp.com/spaces
3. Search for a space thst has a confirmed booking on a specific date
4. Click on that space
5. Attempt to select the already confirmed date on the date picker

**Test Data**:
- Email: requester@example.com
- Password: Password123
- A space with a confirmed booking on a known date

**Expected Result**:
The confirmed date is greyed out and cannot be selected.
