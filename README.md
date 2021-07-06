# SpeedVote
A highly scalable and available mobile voting system.

![Architecture Diagram](docs/SpeedVoteArchitecture.png)


## Users
- Admin (Config and Internal User management)
- Election Officer (Poll creation)
- KYC Officer (Manual user verification)
- Voter (General public, poll participants)

## Workflows
Public workflows - internal user management will be discussed in a separate document

### User Registration
- Anonymous user applies for an account using a unique email or mobile number
- Once verified, he/she will then need to submitt a face photo+video and signature as well as his personal details matching the national identification system
- Additionally he will need to pick his locality information, as well as enter some personal information
- A verification request is sent to the KYC Officer
- The KYC officer approves the verification status of the user
- The user is now a legit Voter

### Election
- Election Officer prepares the Questions
- Election officer locks down the Questions and broadcasts them to the user (at this point the questions are prepared but not yet ready for use)
- After the "unlock time", the users are now allowed to participate in the election process
- Before the "deadline", users will no longer be allowed to vote
- When the user "locks" the vote, he will no longer be allowed to vote and all the related information needed to verify his vote will be uploaded to S3 as well as duplicated in DynamoDB
- The actual casting of the ballot will involve fetching the user's current location as well as a "selfie video" to verify his identity together with a signature. In case of election protests/recounts, the raw file will be used for manual verification
- Make sure S3 is locked for editing and deletion (s3 object lock)

### User Activity
- all user activity will be tracked (realtime stream)
- live dashboard for current poll (estimated based on the stream of live activity)

## Tech Stack
- CloudFormation
- DynamoDB
- Lambda
- Cognito
- AppSync
- Kinesis Firehose
- S3

## Architecture
```
<insert diagram for recording real-time user activity>
<insert diagram for casting the actual ballot in the poll>
```
