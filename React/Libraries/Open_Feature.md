### Feature flags
- vendor-agnostic, community driven API for feature flagging
- **feature flags** are, in a sense, if-else statements that can be controlled at runtime. It allows to alter application behavior without redeploying a new code.
- - A practical showcase would be an user who has paid for a feature. The code would contain `const isAllowedToUseFeature = useFeatureFlag('paid-feature')`
- Good example of provider is [Flagd](https://flagd.dev/installation/) service.

### React + Open feature
In Flagd we would have saved specification for our feature flags (I use .yaml file but it can be connected to eg. a database as well)
```
// Flagd
{
  "flags": {
    "welcome-message": {
      "variants": {
        "on": true,
        "off": false
      },
      "state": "ENABLED",
      "defaultVariant": "off"
    }
  }
}
```

```
// React application
import { useBooleanFlagValue } from '@openfeature/react-sdk';

export function MyComponent() {
    // boolean flag evaluation
    const isNewMessageVisible = useBooleanFlagValue('new-message', false);

    return (
        <div>
            {isNewMessageVisible ? <MessageComponent /> : "No new message"}
        </div>
    )
}
```

- Using feature flag mechanism, features can be controlled without redeploying app OR deploying app with not finished features early without users seeing them, giving you big leverage test how the feature behaves in production environment.
