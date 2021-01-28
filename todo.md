- Authentication via cognito (based on Udemy Vue course).
- Finish frontpage UI to accept an M3U.
- Hook up lambda function that will store M3U contents in S3.  
  Figure out how to pass auth token to Lambda.
- Add list of archives to frontpage.
- Create separate API that will provide WMBR archive list.
  format: json
  need: how to parse https://wmbr.org/cgi-bin/arch
  run: once a day to repopulate from scratch a DynamoDB collection.
- Add "I'm feeling lucky" button that will pick random item from archive.
- Add lookup widget that will search through archive list dynamically.
