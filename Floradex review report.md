# Report from Floridex's proposed architecture review.

## Overview

During the inspection of Floradex's proposed architecture (10-16-2012) the following issues were raised.

### Missing [schema](http://en.wikipedia.org/wiki/Database_schema)

**Issue**

While schema might have been left out in favor of the design, it was felt that the schema has too much effect on the other components of the architecture to not be considered now. Specifically, because this application is meant to deal primarily in information, understanding what information needs to be sent will effect any interactions the database has with the rest of the application.

**Must fix**: without an at least abstract schema, we cannot confidently analyze the integrity of the rest of the architecture.

### Server/database details

**Issue**

Details were missing regarding where the database will be stored. The architecture discussed hosting a central server with synchronized local copies of the database, but did not investigate or come to a solid decision. While this and also non-synchronized options are all possible, we wish to see a clear choice and an analysis of the pros and cons of said choice. We would expect to see diagrams of the information being passed between any databases and the other components. We also recommend considering how the applications information will potentially be updated.

**Must fix**: We must know whether the application must interact with a central server, and when, how, and for what purposes the applications fetches data, in order to create a complete architecture.

### The "wiki"

**Question**

The wiki was ultimately a misunderstanding, and meant linking to Wikipedia pages for further information. However, it was also mentioned that a future, more fully featured version of the application might include their own hosted wiki, to allow users to contribute.

**Comment**: As the wiki is ultimately not a component in the architecture, no further action is required other than clarification on the architectural overview. However, we recommend coming to a firm conclusion about future intents regarding a dedicated wiki, so that if this is planned, any interfaces may be written to accommodate such an update.

### Structure of the information

**Issue**

No details were given regarding how the data will be passed amongst different components of the application. Mentioned possibilities were JSON and XML.

**Must fix**: Information passing will be the majority of the application's services. In order to create a complete picture of how components will communicate, we must determine what "language" they will speak.

### Search

**Question**

Search appeared to have been taken for granted in the review. The submitters mentioned that there were many details already figured out but left out as design details instead of architectural details. However, algorithmic details are architectural as they will determine what information the feature requires in order to function.

**Must fix**: This issue treads into design territory; however, we specifically wish to see when and how the search will communicate with the database.

### UI mockup

**Defect**

A typo was found that the buttons switched on the last slide.

**Comment**: The submitting team indicated that they were aware of this typo. No other issues were raised regarding the UI! :)

## Conclusion

Our final conclusion is that this architecture cannot be approved without another meeting. Before said meeting, we require that Floradex submit a detailed architecture regarding the database components and related interactions, including a schema. We strongly recommend including diagrams modelling these database interactions.

**Requires another meeting**