Quiz III
Build a bidding website with a Rails JSON API and a React client.

Submission Guidelines
This project will have a Rails application and a React application. Make sure

both directories are included in the same Git project like so:

final_exam/ <--- Run git init here

  |

  +-- .git/

  +-- biddr_api/ <--- Rail application in here

  +-- biddr_client/ <--- React application in here

Generate the React app with create-react-app and generate the Rails app _skipping git_ with rails new --skip-git biddr_api. If you choose to generate your Rails app with the --api option, be aware that the session will be removed. To re-add the session, check out this article.

Commit and push your work. Then, create a new branch to implement the following features.

Part 1: Rails HTTP API – Auction and Bid CRUD
Value: 20%

Build a Rails JSON API. Based on the wireframes, at the bottom of this page, choose which columns you will need for your application's models.

Implement create, show and index actions for Auctions.
Auctions should have many Bids.
Implement the create action for Bids.
You should use a tool like Postman to manually test your API at this point.

Part 2: Rails HTTP API – User Authentication
Value: 20%

Add user authentication.

Implement a SessionsController.
Add a create action to sign-in users.
Add a destroy action to sign-out users.
Only authenticated users can:
Create auctions.
Create bids.
Users must be associated to the auctions and bids they create.
Part 3: React Client – Public Routes
Value: 20%

Build a React Client for the JSON API. Use the wireframes below as a guide.

Implement the following page components:
WelcomePage display welcome text.
AuctionIndexPage lists all auctions.
AuctionShowPage shows a single auction. the AuctionShowPage is illustrated in the wireframes.
Create a NavBar to navigate between WelcomePage and AuctionIndexPage.
Wireframes
WelcomePage


AuctionIndexPage


AuctionShowPage


Part 4: React Client – Sign In
Value: 15%

Add support in the client for user authentication:

Implement a SignInPage and link to it in the NavBar.
Only show the SignInPage link if the user is not signed in. Otherwise, display their name.
Submitting the form on the SignInPage updates the session cookie and updates the React application state with the user.
Wireframes
SignInPage


Part 5: React Client – Auctions and Bidding
Value: 15%

Add support for auctions and bids in the client:

Implement the AuctionNewPage shown below to allow authenticated users to create bids.
After successfully creating a new auction, redirect the user to its AuctionShowPage.
Implement the ability to bid on auctions from the AuctionShowPage.
Wireframes
AuctionNewPage


Part 6: React Client – Authenticated Routes
Value: 10%

Create a component to redirect users attempting to access unauthorized routes.

Create a AuthRoute component based on react-router-dom's Route component.

AuthRoute takes an isAllowed prop. When the prop is true, let the route render the given component. When the prop is false, redirect the user to the SignInPage. In all other respects, it functions like the Route component.

Use it to prevent users from accessing the AuctionNewPage if they are not signed-in.

Bonus 1: Sign out
Value: 10%

Add the ability for users to sign out.

Add a Sign Out link to the NavBar that is only shown to signed-in users.
Clicking it signs out the user. Removing them from the application state and removing their id from the session cookie.
Bonus 2: Sign Up Page
Value: 10%

Add the ability for users to sign up from the frontend client.

Implement a UserController with a create action to allow users to sign up through the API. Creating a user should also sign in the user meaning that the create action must return a JWT.
Implement a SignUpComponent to create a user.
Add a link to the SignUpComponent in the NavBar if the user isn't signed in.
Bonus 3: Auction States
Value: 5%

Support auction states.

Add support for states, draft, published and reserve met, to the auction model.
When created an auction should be set to the draft state. In draft state, the auction is only visible to the author.
Implement a Publish button, only visible to the author of the auction, in the AuctionShowPage.
When clicked, this sets the auction's state to published. All published auctions should be visible.
When a user bids higher than the auctions reserve price, set the reserve met state on the auction. This can only happen on published auctions.