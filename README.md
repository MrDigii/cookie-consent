# b.lateral Cookie Consent Banner

[![NPM](https://img.shields.io/npm/v/cookie-consent.svg)](https://www.npmjs.com/package/cookie-consent) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

This repository consist of a generic implementation of a cookie consent banner for use in various website projects. The project is split into two versions:

-   Implementation as React component
-   Native Javascript implementation

## Install

```bash
npm install --save cookie-consent
```

## Usage

### Use as React Component

To provide a better workflow with React projects you can import the cookie-consent as a React Component.

```tsx
import React, { Component } from "react";

import MyComponent from "cookie-consent";
import "cookie-consent/dist/index.css";

class Example extends Component {
    render() {
        <Cookie.View>
            {({
                handleAccept,
                handleDecline,
                additionalDeclineProps,
                additionalAcceptProps
            }) => (
                <>
                    <Cookie.Icon src="..." />
                    <Cookie.Title>
                        Verwendung von Cookies für Analyse- und Marketingzwecke
                    </Cookie.Title>
                    <Cookie.Text>
                        Wir verwenden Cookies, ...
                        <a href="datenschutz">Datenschutz</a>.
                    </Cookie.Text>
                    <Cookie.ActionContainer>
                        <Cookie.Action
                            onClick={handleDecline}
                            {...additionalDeclineProps}
                        >
                            Cookies ablehnen
                        </Cookie.Action>
                        <Cookie.Action
                            onClick={handleAccept}
                            {...additionalAcceptProps}
                            type="accept"
                        >
                            Cookies akzeptieren
                        </Cookie.Action>
                    </Cookie.ActionContainer>
                </>
            )}
        </Cookie.View>;
    }
}
```

The `Cookie.View` element holds the entire cookie consent banner. It provides multiple additional properties to customnize the banner behaviour.

| Name                        |   Type   |               Default                |                                           Description                                            |
| --------------------------- | :------: | :----------------------------------: | :----------------------------------------------------------------------------------------------: |
| **className**               |  string  |                  ""                  |                      Name of additional CSS class to style the banner view                       |
| **zIndex**                  |  number  |              undefined               | Value for CSS z-index property. It overrides existing z-index values in external CSS definitions |
| **name**                    |  string  |           "cookie-consent"           |                                        Name of the cookie                                        |
| **lifetime**                |  number  |                 365                  |                                  Lifetime of the cookie in days                                  |
| **urlWhitelist**            | string[] |             Empty Array              |                       List of URLs on which no banner should be displayed                        |
| **consentAcceptStatusMsg**  |  string  | "Akzeptiert am %DATE% um %TIME% Uhr" |            Message that should be displayed to inform about the cookie consent status            |
| **consentDeclineStatusMsg** |  string  | "Abgelehnt am %DATE% um %TIME% Uhr"  |            Message that should be displayed to inform about the cookie consent status            |
| **noCookieStatusMsg**       |  string  |                 "-"                  |            Message that should be displayed to inform about the cookie consent status            |
| **dateFormat**              |  string  |              "dd.mm.yy"              |              Defines how to display date informations inside cookie consent status               |
| **timeFormat**              |  string  |               "hh:mm"                |              Defines how to display time informations inside cookie consent status               |

Inside the `Cookie.View` element it is necessary to define a function with the following props (called RenderProps):

| Name                       |          Type           |                                Description                                |
| -------------------------- | :---------------------: | :-----------------------------------------------------------------------: |
| **handleAccept**           |       () => void        |                 Function to call on consent accept events                 |
| **handleDecline**          |       () => void        |                Function to call on consent decline events                 |
| **additionalAcceptProps**  | {["data-gtm"]: string;} | Object that contains package predefined props for consent accept element  |
| **additionalDeclineProps** | {["data-gtm"]: string;} | Object that contains package predefined props for consent decline element |

## License

MIT © [ic3m3n](https://github.com/ic3m3n)
