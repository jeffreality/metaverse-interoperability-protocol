#The First Pass at a Metapass
##Passport to the Metaverse!

This is the first draft of a metapass data bundle that will be passed back and forth as people travel between metaverses. I am publishing it here for comments and feedback, prior to uploading it to github:

```
{
  "metapass": [
    {
      "version": "0.0.1",
      "identity": {
        "username": "my_user_123",
        "name": {
          "full": "Firstname Lastname",
          "given": "Firstname",
          "surname": "Lastname"
        },
        "gender": "other",
        "email": "test@test.com",
        "phone": "1-213-555-1212",
      },
      "avatar": {
        "gravatar": "b021a8beb0107b0834e280fe52567199"
      },
      "wallets": {
        "eth": "jeffreality.eth"
      }
    }
  ]
}
```

JSON will be the standard used to define the data that will be passed from metaverse to metaverse.

- The version number will define the minimum spec used for backward compatibility.
- Each JSON document will start with a root element (“metapass”, “metapack”, or “metaport”).
- Each root element will be an array of dictionaries, even if there is only ever to be one dictionary in it. This is future-proofing in cases where multiple elements might be needed.
- Instead of dashes, underscores are preferred (due to issues with some languages processing JSON).
- In all cases, internationalizing information is preferred.
- Dates should all be formatted as `yyyy-mm-dd`.
- Gender options: `[male, female, non_binary, transgender_male, transgender_female, other, non_disclose]`
- If any elements are required for your metaverse, the rules should be stored at: `mip.yourdomain.ext` (for example: https://mip.jeffreality.com). - The format will be the same as the data, with boolean values (typically true) instead of data. For example, the following file requests an email address for entry:

```
{
  "metapass_requested": [
    {
      "version": "0.0.1",
      "identity": {
        "email": true
      }
    }
  ]
}
```

If you want to add your own elements, they should be added to a dictionary with a key using reverse domain notation. For example:

(most other data was removed in the example below, to show what was changed)

```
{
  "metapass": [
    {
      "version": "0.0.1",
      "identity": {
        "com.jeffreality.mymetaverse": {
          "version": "2.0.4",
          "username": "jeffreality",
          "my_identifier": "CB254AF"
        }
      }
    }
  ]
}
```

These elements should be added and passed to any data you receive and send, in the expectation that returning users will deliver this information back. It is recommended that you maintain a version number with your data structure. Always make sure you store data from other services, and send it all on when you pass a user to another metaverse.
