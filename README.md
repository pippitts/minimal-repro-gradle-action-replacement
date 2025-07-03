# 36825

## Current behavior

Preset replacements:gradle-wrapper-validation-action doesn't match as expected, so no replacement PR is being made

from the logs showing the action being found
```
DEBUG: packageFiles with updates (repository=pippitts/minimal-repro-gradle-action-replacement, baseBranch=main)
       "config": {
         "github-actions": [
           {
             "deps": [
               {
                 "depName": "gradle/wrapper-validation-action",
                 "commitMessageTopic": "{{{depName}}} action",
                 "datasource": "github-tags",
                 "versioning": "docker",
                 "depType": "action",
                 "replaceString": "gradle/wrapper-validation-action@3",
                 "autoReplaceStringTemplate": "{{depName}}@{{#if newDigest}}{{newDigest}}{{#if newValue}} # {{newValue}}{{/if}}{{/if}}{{#unless newDigest}}{{newValue}}{{/unless}}",
                 "currentValue": "3",
                 "updates": [],
                 "packageName": "gradle/wrapper-validation-action",
                 "warnings": [],
                 "sourceUrl": "https://github.com/gradle/wrapper-validation-action",
                 "registryUrl": "https://github.com",
                 "mostRecentTimestamp": "2024-07-15T19:32:42.000Z",
                 "currentVersion": "v3",
                 "currentVersionTimestamp": "2024-07-15T19:32:42.000Z",
                 "currentVersionAgeInDays": 353,
                 "fixedVersion": "3"
               }
             ],
             "packageFile": ".github/workflows/gradle-wrapper-validation.yaml"
           }
         ]
       }
```

Can specifically see `"datasource": "github-tags",` that is different than what the preset has of `"matchDatasources": ["github-actions"],`

see [replacements.json](https://github.com/renovatebot/renovate/blob/main/lib/data/replacements.json#L679)

## Expected behavior

A PR to replace `gradle/wrapper-validation-action` at version 3 with `gradle/actions/wrapper-validation` at version 3.5.0 would be created.

## Link to the Renovate issue or Discussion

https://github.com/renovatebot/renovate/discussions/36825
