# Requirements 

The main requirements of the application are the following.


### Functional Requirements:
- When a user downloads the application it should ask for passport number which is used in combination with random bytes (App Nonce) to generate a cryptographic commitment sha256(passport_number+nonce)
- This will serve as a privacy-preserving unique identifier for the user of the app.
- Automatic launch in the background when the device is switched on.
- A scanner must constantly scan for other peers (application users) and ping them in case the 2 peers are below a specified threshold of proximity. Additionally, in that case, the interaction should be queued for reporting.
- A listener must listen for pings received from other peers, record it and verify the ping with its own scanner as well.
- The queued interactions on each device must be to a centralised server at regular intervals. 
- P2P Interaction reports must be sent along with the unique identifier of the app's user.
- The peers must somehow coordinate reporting to avoid multiple repeated reports.
- The server that receives the reports, must update and maintain a graph database where each node is a unique app identifier and links are interactions within specified proximity with other nodes. Additionally, each interaction link must have a counter property to distinguish lengthy close interaction from short accidental ones. 
- If any app user is found to be positive to Covid-19, the corresponding health centre should contact the administration to manually update the graph and mark the node as a confirmed case.
- Using nodes marked as confirmed cases, the government can use the graph to track down other app users that have been within close proximity with that user (or technically the app device).
- The administration should be able to sort interactions based on the counter property and notify other high-risk users by a push notification.
- Users who receive notifications that have been in close proximity with confirmed cases, can call their corresponding health services and report that. To verify that these are not spoof/prank calls the users must also report their passport number and app nonce such that the health services can verify their user id.

### Non-Functional Requirements
- Ideally, the application should be cross-platform to maximize reach. 
- The server must be scalable to handle the interactions reports
- The application must not leak any user personal information