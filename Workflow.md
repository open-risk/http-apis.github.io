# Workflow

A developer wishing to design and deploy his/her own data services with Hydra, hydrus (the server) and hydra-agent (the client)
has to go through a workflow that is defined by multiple steps: from defining the best Hydra/RDF/OpenAPI description of the
resources and operations he/she is going to provide, to create the conditions for the services to be deployed by hydrus and for the hydra-agent to access them. 

In general, the workflow is made up of these basic steps:
1. The Developer defines an API description in the shape of an RDF-compliant or Hydra-compliant JSON-LD (Hydra is an RDF vocabulary itself) or in
shape of an OpenAPI data structure (yet to be implemented). Any shape that is supplied it is parsed into an Hydra-compliant JSON-LD that
becomes the API documentation (in Hydra slang, the `ApiDoc`). Every REST resource is an `HydraClass`.
2. hydrus toolkit parses the `ApiDoc` and defines handlers to support the pusblishing of the resources as described. It put in place
a system for credentials management to secure the endpoints with Two-factors token authentication. Every `HydraClass` has its
endpoint and HTTP methods and related operations as defined by the documentation.
3. hydra-agent reads the `ApiDoc` via the entrypoint and parses the JSON-LD into an internal representation (RDF graph) that allows
the client to proceed to query the endpoints for its searching, storing or retrieving necessities. The internal representation
may change depending from the different `ApiDoc` that the clients reaches.

<under construction>