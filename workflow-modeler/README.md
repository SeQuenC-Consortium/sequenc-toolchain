# Workflow Modeler & Camunda Engine

## Docker Compose

The `docker-compose` file contains many components, where some of them are optional and some of them are necessary. Depending on the use-case, the necessary parts for model and executing workflow with the unification layer are:

| Container   | Description |
| ----------- | ----------- |
| workflow-modeler      | Used to model the workflow with different tasks and the QuantME Framework.      |
| camunda-engine   | Necessary to execute the workflow. |

The `workflow-modeler` has several registered endpoints, which can be used as environment variables to connect to the respective services.
In the most basic setup with `qunicorn-core` only the qunicorn-core setup need to be started.