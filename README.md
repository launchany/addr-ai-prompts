# Prompt Starters for AI-Assisted API Design

Example prompts are provided below to help you get started with your own AI-assisted API design coach session using the [ADDR API design first process](https://addrprocess.com). This process is the first step in transforming requirements into an API design contract that will help drive your spec-driven design efforts. 

The ADDR process has been developed over the last decade and has been fully documented in the book, ["Principles of Web API Design: Delivering Value with APIs and Microservices"](https://www.informit.com/store/principles-of-web-api-design-delivering-value-with-9780137355631) (Addison-Wesley 2021).

These starter prompts are used in our quarterly report that evaluates LLMs to determine the best fit to help coach you in an outcome-based API design. 

[Download the latest report](https://launchany.com/ai-assisted-api-design-report), a definitive guide to using LLMs as API Design Coaches, not just code generators. 

## Tips and Guardrails

* __Separate chat sessions when needed__. For some models, you may need to separate each phase into a separate chat session. In that case, export the artifacts from each previous chat session and import all artifacts into the next chat session. This will reduce hallucinations or sessions that turn sloppy or run amok. 
* __Prefer iterative work over one-shot design sessions__. The larger the scope of your project, the more bounded API contexts you may have. When you have more than one, limit the model to operating on the first boundary in its list (or a boundary of your choosing) before proceeding to each boundary in turn. Failing to take this approach often yields poor results or incomplete responses. 
* __Ask the model to generate your style guide prompt__. When you are ready to turn your ADDR artifacts into an API design, launch a separate chat session and ask the model to generate a prompt from your style guide. This will help you to align your designs to your organization's API style guide during design and reduce the amount of API design review that is required.

NOTE: Each starter prompt will need to be supplemented by your own prompting as you progress through each phase to direct the model to change, remove, or add anything that may be missing. 

## New Chat Session Prompt

This prompt is critical to establish the role of the model, the steps we will take, and that we will focus on requirements prior to starting the ADDR process. Reviewing requirements first helps to spot gaps and also helps to drive the API design effort. 

```
You are an API architect that needs to translate requirements into an API design. First, I will ask you to review and help me to refine the requirements. Then we will use ADDR for the API design first methodology. 

We will be designing a bookstore API. 

However, before we start ADDR, I need some help refining the requirements. Once we validate that the requirements are sufficient, then we will start the ADDR process. 

I will provide initial requirements next. 
```

## Requirements Clarification Before ADDR

This is an example of our bookstore with minimal requirements. In this case, the model _should_ focus on identifying critical gaps.

```
Here are the initial requirements: 

* Online ecommerce store that only sells books
* Called JSON’s Bookstore
* Must design a series of APIs to support online commerce that includes shopping and checkout capabilities
* We will also need order fulfillment, order tracking, inventory management, and catalog management capabilities in the future
* The API also needs to support integration with partners and customers.
* The API will support a web interface, mobile app, and third-party API consumers 
* Initial Scope: Design APIs to support online shopping and checkout.
* Future Scope: Order fulfillment, order tracking, inventory management, and catalog management.

Let's hold off on non-functional and technical requirements and focus on the business requirements for now. 

Ask me up to 5 questions that will help to expand and clarify the requirements before we proceed with API design. You may ask two more sets of 5 questions each, if they will help you. If you have everything you need, you may stop asking questions prior to the end of the three sets of questions. 

Once all questions have been answered, summarize the business requirements.

Do not transition into the align phase until I am ready. 
```

### Full Requirements for Bookstore

This is a more comprehensive set of requirements. The model _should_ dig a bit deeper as the high-level requirements are captured. This will result in more detailed refinement and may or may not exceed the scope of the effort.


```
JSON’s Bookstore — Business Requirements Summary:

Initial Scope: Design APIs to support online shopping and checkout.

Future Scope: Order fulfillment, order tracking, inventory management, and catalog management.

Products & Catalog 
• Physical books, e books, audiobooks, special editions, and fixed set bundles. 
• Rich metadata: title, author, ISBN, genre, format, price, language, plus previews, reviews, ratings, and recommendations. 
• Search & filter by book/author details, price range, and format. 
• Catalog managed internally; imports from third party sources as an admin task. 

Commerce Rules 
• Discounts and coupons supported; no loyalty program at launch. 
• Credit card payments only. 
• Returns & cancellations allowed for both physical and digital products within 30 days. 
• Pre orders charged immediately; cancellable until fulfillment. 
• Prices stored tax exclusive; tax calculated by customer location. 
• Multi region support with varying tax rules. 

Fulfillment 
• Physical fulfillment assumed in house or via logistics partner. 
• Digital fulfillment handled by a separate fulfillment app. 

Integrations 
• Partner APIs for catalog and inventory queries only (no ordering). 
• Web, mobile, and third party API consumers supported.

Proposed Primary User Journeys (Business View):

1. Customer Browsing & Discovery 
• Browse catalog by category, format, or curated lists. 
• Search with filters (author, title, price, format). 
• View detailed product pages with rich content. 

2. Shopping & Checkout 
• Add items (including bundles) to cart. 
• Apply discounts or coupons. 
• Checkout as guest or logged in user. 
• Provide shipping/billing info. 
• Pay via credit card. 
• Receive order confirmation. 

3. Order Management 
• View order history (for logged in users). 
• Cancel orders or pre orders before fulfillment. 
• Request returns/refunds within 30 days. 

4. Pre Order Flow 
• Place pre order for upcoming releases. 
• Immediate payment capture. 
• Cancel any time before fulfillment. 

5. Partner Integration 
• Partners query catalog and inventory availability. 
• No ordering capability for partners.

Let's hold off on non-functional and technical requirements and focus on the business requirements for now. 

Ask me up to 5 questions that will help to expand and clarify the requirements before we proceed with API design. You may ask two more sets of 5 questions each, if they will help you. If you have everything you need, you may stop asking questions prior to the end of the three sets of questions. 

Once all questions have been answered, summarize the business requirements.
```

### Generate Initial User Journeys

Once your requirement are completed, you may offer existing user journeys or ask the model to help you identify them. In either case, this will help to shape the job stories we create in the Align phase. 

You may choose to skip this step if your requirements, above, already contain common user journeys or workflow steps. 

```
Next, propose the primary user journeys we should model based on these requirements. Each journey should contain a title, goal, and the journey steps. Avoid including steps that a user performs to interact with the browser (e.g., scrolling, viewing, inspecting, reviewing, prepares, becomes available, considers, initiates). Each step must be an actor action such as submits, searches, requests.
```

## Start the Align phase

This prompt helps to transition from requirements clarification to the Align phase. The prompt asks for the model to explain the process first, helping those new to ADDR to understand what should be created in this phase. It also helps to reiterate the model's understanding of the process, to ensure it will move through the Align phase successfully. Finally, it establishes expectations of what needs to be completed before moving into the Align phase.

```
Ok, let's proceed to the Align phase of ADDR. Remember, we are API architects that need to translate requirements into an API design. Here are the rules and restrictions for this effort: 

* Until I tell you otherwise, let’s stay in the Align phase and not blend any activities from the other phases of ADDR 
* By staying only in the Align phase, we will need to compose a set of unifying job stories and associated activities and activity steps 
* Job stories will use the standard format of WHEN, I WANT TO, SO I CAN 
* Job stories should be unifying job stories, meaning that they have a clear and broad scope sufficient to result in an outcome rather than completing a task 
* Job stories must be numbers JS1..n for easy reference between us and between artifacts 
* Activity steps are actions that the user will perform via the API. Do not include any UI-specific actions by the user, such as scrolling, reading, paging through results. Focus on action-specific steps 
* The activity steps will be grouped into activities, which map to capabilities 
* We will not consider the Align phase complete until we have both artifacts completed 
* We will use business language that benefits the API consumer rather than any internal or operational terms 
* We will not focus on anything related to HTTP yet 
* When we have determined that we have completed the Align phase, you will package the final Align deliverable as a single, clean reference sheet so it’s ready for hand off to the Define phase 

Let’s start by having you explain the phase, these artifacts, and why it is important so that we are clear. 
```

### Create Unifying Job Stories

```
Now that we're aligned on the process, we can begin creating the first set of artifacts.

Using the requirements above, let's write one or more unifying job stories for each of the major flows. Remember that job stories capture jobs to be done rather than steps in a process, so let's keep them high-level. Be sure to number the job stories using the format JS1..n, so that we can refer to them easily as we work through the ADDR process 

A job story should use the format: 

When [situation], I want to [motivation], so I can [expected outcome].

Avoid feature-centric job stories. Ensure the job stories are consolidated as needed to create higher-level unifying job stories.
```

 If needed, use your own prompts to edit, remove, or modify the recommended job stories.
 
 Once you have reviewed your job stories, you may proceed to mapping the activity steps for each job story.

### Expand job stories with activity steps

Next, expand your job stories into the activity steps needed to accomplish each job to be done:

```
Let’s break each unifying job story down into the activities and activity steps that are required to go from the situation to the expected outcome. Avoid including steps taken in a UI such as scrolling or entering criteria, instead focusing on the action of submitting the criteria. Remember that activities represent milestones or incremental groups of work, while the activity steps represent a single action taken. Produce a table with the results using the following columns: Job Story ID, Activity, Activity Step, Description
```

## Validate the Align Phase

Let's finalize the Align phase by ensuring that we have covered all necessary areas before proceeding. We can always go back and make changes, but this helps us to spot any obvious gaps before proceeding to the Define phase. 

```
Validate the produced artifacts and recommend any areas that could be improved or any gaps that may wish to be addressed. I will then review them and let you know if any of your recommendations should be applied. 
```

## Package up the Align Phase Artifacts

Optionally, you can request the model to package up all artifacts. This will allow you to make an archive before proceeding. Should the model get off track and you need to start a new session, you can use this package to get the model up-to-speed on decisions made so far:

```
Package the final Align phase deliverable.
```

## Start the Define Phase

Like the Align phase prompt, we will now tell the model to move into the Define phase, define the expectations, and have it remind us about what we need to do in the Define phase:

```
The Align phase is now complete. Let's start the Define phase. Here are the rules and restrictions for this effort:

* Until I tell you otherwise, let’s stay in the Define phase and not blend any activities from the other phases of ADDR  
* By staying only in the Define phase, we will need to identify the API boundaries and compose an API profile for each API that we have identified  
* We will not consider the Define phase complete until we have identified the boundaries and composed API profile(s), API resource(s), published Event(s) for each API operation, identified the API resource relationships, and a sequence diagram or sequence example of how the API would be used to complete each job story  
* API boundaries will be summarized in a table that contains the following columns: Boundary Name, Boundary Description, Job Story(s)  
* API profiles will be summarized in a table that contains the following columns: Operation Name, Description, Participants, Resource(s), Emitted Events, Operation Characteristics, Operation Details  
  * The Operation Name will be in the format of operationName()  
  * The Participants include one or more roles or personas that will need access to the operation  
  * The Resource(s) include the primary and possible secondary resources involved in the operation  
  * Emitted Events includes one or two events that the API will publish when the operation completes successfully, allowing for future   
  * Operation Characteristics identifies the safe, unsafe, or idempotent design of the operation, and if the operation should be designed as synchronous (default) or asynchronous  
  * Operation Details include the request and response values, such as identifiers, resource representations, and filters. Keep in mind that we don’t want to design the HTTP details yet, so let’s keep this to basic details  
* API resources will include a business-friendly name and a list of properties. Keep in mind that we aren’t ready to define the schema details yet, so don’t include any JSON schema details just model the resource independent of HTTP or design details  
* Emitted Events should include at least one event in most cases using the format of ResourceName.EventName. For example, Project.Created  
* We will use business language that benefits the API consumer rather than any internal or operational terms  
* We will not focus on anything related to HTTP yet  
* We will identify boundaries that benefit the API consumer rather than the API producer, to ensure a better developer experience (DX) and cohesive API profiles  
* When we have determined that we have completed the Define phase, you will package the final Define deliverable as a single, clean reference sheet so it’s ready for hand-off to the Design phase

Let’s start by having you explain the phase, these artifacts, and why it is important so that we are clear. 
```

### Find Candidate Boundaries

Next, we want to identify candidate boundaries. Many models will generate a boundary per job story. Depending on the granularity of your job stories, this may or may not be your desired approach. Adjust the prompt as needed to find the balance between boundaries vs. creating a requirement of moving API consumers between boundaries. 

```
Recommend any candidate boundaries as a first version of the boundaries table. Then, provide a summary of why the boundaries work and any additional considerations, including overlap or boundaries that could be unnecessary based on requirements provided. 

Be sure to suggest boundaries that align with a better developer experience rather than strictly aligning boundaries to domain concepts. 

Use the principles advocated by Vaughn Vernon—including Bounded Contexts, Aggregate design, autonomy, domain events, and the risks of premature distribution—to identify clear API boundaries for the domain described below.

Your goal is to determine where one API or service boundary should end and another should begin, based on the business domain, invariants, consistency needs, and language differences within the domain.

## **Rules for Identifying API Boundaries**

### **1. Do *not* distribute a single domain model across APIs**

Look for areas where splitting the model would require synchronous remote calls.
If so, keep them together.

### **2. Each API corresponds to a single Bounded Context**

A boundary is valid only if it represents:

* a distinct domain language
* a cohesive responsibility
* its own invariants
* its own data ownership
* independent lifecycle and scaling needs

### **3. Invariants must be enforced *within* a boundary, not across them**

If enforcing a rule requires strong consistency between two concepts, they belong together.

### **4. Avoid synchronous cross-boundary calls during domain operations**

Cross-boundary communication must *not* be needed for:

* validations
* invariant checks
* business rules
* transaction completion
  If it is needed, merge the boundaries.

### **5. Prefer asynchronous, event-driven integration**

If collaboration can be achieved via domain events and eventual consistency, boundaries may safely be separated.

### **6. Require model-to-model translation at boundaries**

If two areas use different terms, structures, or mental models for the same concept, they belong in separate contexts.

### **7. Don’t create boundaries just because they could be microservices**

Distribution increases complexity. Justify boundaries only if they enable:

* autonomy
* team alignment
* isolated change
* meaningfully different scaling needs
* distinct language

### **8. Favor small, autonomous Aggregates**

Aggregates must:

* have clear transactional boundaries
* operate without external synchronous calls
* enforce their own invariants
  This supports distributed API modeling.

## **Required Output**

### **A. Recommended API / Bounded Context Boundaries**

For each proposed boundary, include:

* **Context Name**
* **Purpose / Responsibility**
* **Core Entities / Aggregates**
* **Key Invariants**
* **Why it is separate from other boundaries**
* **Expected API responsibilities (inputs/outputs)**

### **B. Boundary Rationale**

Explain the reasoning using DDD concepts such as:

* linguistic differences
* consistency requirements
* autonomy
* event-driven integration
* team alignment
* aggregate independence

### **C. Integration Model Between Boundaries**

Describe how boundaries collaborate using:

* domain events published
* domain events consumed
* anti-corruption layers (ACLs)
* asynchronous vs. synchronous patterns
* any unavoidable synchronous calls and their justification

### **D. Pitfalls to Avoid**

Identify splits or designs that would cause:

* distributed monolith behavior
* chatty network calls
* cross-boundary invariants
* tight coupling
* leakage of domain logic via APIs
* shared domain models across contexts

```

```
Should some of the boundaries be combined to ensure cohesion in how we consume APIs to satisfy the job stories?
```

### Identify API Resources

Before generating API profiles, it is useful to capture the conceptual resources that the API(s) will manage. Doing so will help the model move forward with acceptable recommendations in most cases. 

```
Let’s proceed to identifying the API resources we will need by reviewing the job stories and activity steps. Remember, we don't want schema definitions, just tables with the resources and recommended properties, relationships to other resources. Expand this into a Resource Definition Table for each boundary, including relationships between each resource.
```

### Generate an API Profile For Each Boundary

Now we want to generate an API profile for each boundary. This prompt includes some operational characteristics, which will inform our API design in the next phase. 

```
Let's generate an API profile for each boundary, proposing a business-friendly name and description for each API that denotes its scope and purpose along with the API operations mapped from the related activity steps. For the characteristics column value of each operation, use "safe" if read-only, "unsafe" if the operation isn't idempotent, or "idempotent" if the operation should be idempotent. Also include "sync" or "async" based on whether the operation will return results or need to operate in the background. Finally add "bulk import" only if the operation is performing a bulk import of data.
```

### Validate API Profiles

Before we diagram the workflows using our API(s), this prompt will look for any gaps or improvements. Sometimes models will miss creating things, such as an Order or Cart. Have the model check itself and perform your own review before proceeding.

```
Review the API profiles and identify any gaps or improvements for consideration
```

Instruct the model to apply any recommendations that you wish to incorporate. 

### Generate sequence diagrams For Each Job Story

Next, request the model to generate sequence diagrams for each job story. This helps to identify gaps, finds areas that may overlap and require adjusting boundaries (and thus API profiles), and helps to visualize how the API(s) will collaborate together to deliver job stories. 

```
Looks good. Generate the sequence diagrams for each job story using Mermaid format to show the progression from the WHEN to the SO I CAN - use the API operation names
```

## Package up the Define Phase Artifacts

Optionally, you can request the model to package up all artifacts. This will allow you to make an archive before proceeding. Should the model get off track and you need to start a new session, you can use this package to get the model up-to-speed on decisions made so far:

```
Package the final Define phase deliverable.
```
## Start the Design Phase

```
The Define phase is now complete. Let's start the Design phase. Here are the rules and restrictions for this effort:

* The Align and Define phases have been completed already
* Until I tell you otherwise, let’s stay in the Design phase and not blend any activities from the other phases of ADDR  
* By staying only in the Design phase, we will be required to produce a high-level API design  
* For this design, let’s assume we will use RESTful practices and leverage the HTTP protocol, including HTTP methods, response codes, and headers, appropriately  
* We will not consider the Design phase complete until we have the high-level API design artifact complete for each API profile provided from the Define phase  
* Each high-level API design will be summarized in a table that contains the following columns: HTTP Method, Resource Path, Operation Name, Description, Request, Response (Success), and Response (Error)  
  * The Request and Response columns will contain details about input and output data related to query filters, identifiers, and resources referenced  
  * The Response (Error) column should include the proper 2xx success code based on the operation type and any 4xx family of HTTP response codes that the operation might produce  
* API operations have already been identified in the Define phase artifacts, which will be provided  
* Be sure to select the appropriate HTTP method based on the characteristics of each operation  
* When we have determined that we have completed the Design phase, you will package the final Design deliverable as a single, clean reference sheet so it’s ready for hand-off to the Refine phase

Let’s start by having you explain the phase, these artifacts, and why it is important so that we are clear. 
```

### Establish Your Design Style Guidelines

The prompt below establishes the REST-based design styles that should be applied. You may wish to replace this prompt with your own set of design preferences. However, this prompt contains a common set of guidelines that we have used for a variety of organizations. 

```
Use the following design style guidelines when designing the API:

1. General API Principles:
    * Design APIs to be intuitive, consistent, and interoperable within an open ecosystem.
    * Follow RESTful principles, ensuring each API is a well-defined resource with appropriate HTTP methods.
    * Default response format must be JSON, adhering to RFC8259 standards.
2. URL and Resource Design:
    * Base path structure: {business-domain}/{v#}/{resource-type}/{id}.
    * URLs must be human-readable, avoid application-specific names, and use hyphen-delimited business domains.
    * Major version (v#) must be included and follow a whole-number format (e.g., /v1/).
    * Resources should be nouns in plural form (except singletons) and use UUIDs as identifiers.
3. HTTP Methods and Functional Resources:
    * Use standard HTTP methods:
        * GET: Retrieve resources.
        * POST: Create resources or execute commands (Use a verb name for the function, e.g. search, but do not use $ prefix for functions).
        * PATCH: Partially update a resource.
        * PUT: Full resource replacement (limited usage).
        * DELETE: Remove a resource and return 204 No Content (no response body).
    * Functional endpoints (e.g., /resource/search, /resource/validate) must be invoked with POST.
4. Query Parameters & Filtering:
    * Use lowerCamelCase for query parameters.
    * Filters must support:
        * AND conditions for multiple parameters.
        * OR conditions using comma-separated values.
    * Reserved functional parameters start with _ (e.g., _include).
    * Sorting must be indicated using sort:
        * Example: GET /v1/orders?sort=createdDate.
5. Response Handling and Standardization:
    * Use HTTP status codes appropriately:
        * 200 OK: Successful retrieval of resources.
        * 201 Created: New resource created; response must contain the full resource representation.
        * 204 No Content: DELETE must return 204 No Content, not a message.
        * 400 Bad Request: Invalid request.
        * 404 Not Found: Resource does not exist.
        * 409 Conflict: Business validation failure.
        * 500 Internal Server Error: Unexpected issues.
    * POST, PUT, and PATCH responses must include the full resource representation rather than a success message.
    * JSON responses must avoid envelope-wrapping (e.g., {"status": "success", "data": {...}} is not allowed).
6. Data Formatting & Serialization:
    * Dates must follow RFC-3339.
    * Use ISO 8601 for durations and intervals.
    * 64-bit integers exceeding JavaScript limits must be returned as strings.
    * Collections must be JSON arrays with each item containing a resourceId.
7. Security & Compliance:
    * Do not pass sensitive data via query parameters; use POST for searches involving PII.
    * Support OAuth 2.0 and API keys for authentication.
    * Implement CORS with appropriate access controls.
8. Pagination & Sorting (Offset-based Pagination):
    * Use offset to specify the starting position (zero-based index).
    * Use limit to define the number of instances to fetch.
    * Default values should be defined in the API specification.
    * Sorting must be indicated via sort. Example: GET /v1/orders?offset=20&limit=10&sort=createdDate
    * Retrieves 10 orders starting from the 21st record, sorted by createdDate.
9. Error Handling & Problem Details:
    * Use RFC 9457 Problem Details (formerly RC 7807) format for error responses.

Repeat your understanding of this design style guide first, then I will let you know if we are aligned and ready to generate the API designs based on our Define artifacts.
```

### Produce an API Design for Each API Boundary

Unlike past prompts, we will ask the model to design an API for the first boundary. We can then proceed for the remaining boundaries if everything looks good. This allows you to progressively review and adjust your style guide prompt. 

If you have a validated style guide prompt from the previous step, you can adjust the prompt to generate all boundaries at once. 

```
Start with the first boundary, drafting its high-level API design table from the Define operations provided. Apply the style guide I provided to you and do not deviate from it. Once we agree on the format and level of detail, we can apply it to the rest for consistency.
```

## Validate the Design Phase Artifacts

After all boundaries have been designed, ask the model to review and locate any gaps. 

```
Review the API designs and identify any gaps or improvements for consideration
```

## Package up the Design Phase Artifacts

Optionally, you can request the model to package up all artifacts. This will allow you to make an archive before proceeding. Should the model get off track and you need to start a new session, you can use this package to get the model up-to-speed on decisions made so far:

```
Package the final Design phase deliverable.
```

## Start the Refine Phase

```
The Design phase is now complete. Let's start the Refine phase. Here are the rules and restrictions for this effort:

* The Align, Define, and Design phases have been completed already. I will attach those artifacts separately  
* Until I tell you otherwise, let’s stay in the Refine phase and not blend any activities from the other phases of ADDR  
* By staying only in the Refine phase, we will be required to produce an OpenAPI Specification of each API and a README document that demonstrates HTTP request/response examples for each job story  
* We will not consider the Refine phase complete until we have completed the artifacts for this phase  
* When we have determined that we have completed the Refine phase, you will package the final Refine deliverable as a single, clean reference sheet so it’s ready for hand-off to the delivery team

Let’s start by having you explain the phase, these artifacts, and why it is important so that we are clear. 
```

## Generate the OpenAPI Document

This prompt requests an OpenAPI document for the first API. This is important, as you will want to review the generated document and perhaps refine the output first before proceeding with any additional APIs. Request the model to generate the remaining OpenAPI specs when you are ready. 

Note that this step is typically a heavy task to perform manually. Using an LLM to generate these files will speed up your feedback loops considerably. 

```
Generate a fully compliant OpenAPI 3.0 specification that reflects the API profile previous created and also aligns with the job stories and activity steps submitted previously and that adheres to the API design standards described above. Include required fields and examples for each property. Examples should be consistent across operations when possible, to demonstrate a basic workflow. Group operations under a tag and include tag meta data to properly document each group of operations. Start with the first API. 
```

## Generate a README Example

Next, we will have the model generate README-based documentation examples for each job story. This helps to show the overall flow without requiring any mocking or a completed implementation, encouraging fast feedback.

Note that this step is typically a heavy task to perform manually, much like the OpenAPI document generation. Using an LLM to generate these files will speed up your feedback loops considerably. 

```
Let’s produce README-based request/response examples using Markdown for each of the job stories that demonstrate the use of the API design to complete the job story. Include the HTTP request format as well as a cURL example for the request, along with an example response. 
```

## Generate a Mermaid.js Sequence Diagram

Next, we will ask the model to generate sequence diagrams that incorporate the API design elements. This will look much like the ones from the Define phase, but with HTTP semantics.

```
Let’s produce sequence diagrams (mermaid format) for each of the job stories that demonstrate the use of the API design. 
```

## Generate Postman Collections

Finally, we will ask the model to generate example Postman collections that mimic the sequence diagrams. This will help technical and non-technical users familiar with Postman to work with mock and production-ready APIs as the delivery process progresses. 

```
Let's produce Postman collections for each of the job stories, following the flow of the sequence diagrams.
```

