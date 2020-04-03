# overview

i am a serverless noob, so i don't think this is a bug per say, but more of me not understanding how things work.  i have searched through the issues and docs and have not come up with a way to make this work correctly.  i am having a sort of "which came first, the chicken or the egg" problem.

### issue at hand

to see issue, just run the following command
```
sls deploy
```

you will get an error with this message
```
Serverless Error ---------------------------------------

  Stack with id serverless-cf-reference-issue-dev does not exist
```

if you comment out / remove the following section under the function events, and then run `sls deploy` it will work.  you can than add back the following section and re-run `sls deploy` and it will work!
```yaml
authorizer:
  arn: ${cf:${self:service}-${self:provider.stage}.UserPoolArn}
  scopes:
  - email
```

so how can i reference this cognito pool for authorization without this little hack?
