# Ticket Breakdown
We are a staffing company whose primary purpose is to book Agents at Shifts posted by Facilities on our platform. We're working on a new feature which will generate reports for our client Facilities containing info on how many hours each Agent worked in a given quarter by summing up every Shift they worked. Currently, this is how the process works:

- Data is saved in the database in the Facilities, Agents, and Shifts tables
- A function `getShiftsByFacility` is called with the Facility's id, returning all Shifts worked that quarter, including some metadata about the Agent assigned to each
- A function `generateReport` is then called with the list of Shifts. It converts them into a PDF which can be submitted by the Facility for compliance.

## You've been asked to work on a ticket. It reads:

**Currently, the id of each Agent on the reports we generate is their internal database id. We'd like to add the ability for Facilities to save their own custom ids for each Agent they work with and use that id when generating reports for them.**


Based on the information given, break this ticket down into 2-5 individual tickets to perform. Provide as much detail for each ticket as you can, including acceptance criteria, time/effort estimates, and implementation details. Feel free to make informed guesses about any unknown details - you can't guess "wrong".


You will be graded on the level of detail in each ticket, the clarity of the execution plan within and between tickets, and the intelligibility of your language. You don't need to be a native English speaker, but please proof-read your work.

## Your Breakdown Here

### Ticket 1: Allow Facilities to save custom ids for Agents

#### Description:
Currently, the system uses the internal database id of Agents when generating reports for Facilities. This ticket aims to enhance the system by allowing Facilities to save their own custom ids for each Agent they work with. This will provide flexibility to Facilities and enable them to use their preferred identification system in the generated reports.

#### Acceptance Criteria:
- Add a new field in the Agents table to store the custom id provided by Facilities.
- Modify the user interface to allow Facilities to input and save custom ids for Agents.
- Ensure that the custom id is unique for each Agent within a Facility.
- Update the generateReport function to use the custom id when generating reports for Facilities.
- Validate and sanitize the custom id input to prevent any potential security vulnerabilities or data integrity issues.
- Ensure that the custom id is included in the generated PDF report for each Agent.

#### Effort Estimate: 8 hours

#### Implementation Details:

1. Modify the Agents table:
- Add a new column called "custom_id" to store the custom id provided by Facilities. This column should be nullable.
- Create a unique index on the combination of Facility ID and custom_id to enforce uniqueness within a Facility.

2. Update the user interface:
- Add a field for Facilities to input and save the custom id for each Agent.
- Implement validation to ensure that the custom id is unique within the Facility.

3. Modify the generateReport function:
- Retrieve the custom id from the Agents table instead of using the internal database id.
- Update the report generation logic to include the custom id in the generated PDF.

4. Implement input validation and sanitization:
- Validate the custom id input to ensure it meets any required format or length constraints.
- Sanitize the custom id input to prevent any potential injection attacks or data corruption.

5. Update the documentation and provide instructions for Facilities:
- Clearly explain how to input and manage custom ids for Agents.
- Provide guidance on the format or conventions for custom ids, if applicable.

### Ticket 2: Update existing reports with custom Agent ids

#### Description:
To ensure consistency, it is necessary to update existing reports for Facilities to reflect the custom ids saved for Agents. This ticket focuses on retroactively updating previously generated reports with the new custom Agent ids.

#### Acceptance Criteria:

- Identify all previously generated reports for each Facility.
- Retrieve the custom ids for Agents from the database.
- Update the existing reports to replace the internal database id with the custom id for each Agent.
- Store the updated reports in the appropriate format (e.g., PDF) for future reference.

#### Effort Estimate: 4 hours

#### Implementation Details:

1. Retrieve previously generated reports:
2. Retrieve the custom ids:
3. Update the reports:
- Modify the reports to replace the internal database id with the custom id for each Agent.
- Ensure that the formatting and layout of the reports remain intact.
4. Store the updated reports:
- Save the updated reports in the appropriate format (e.g., PDF) for future reference.
- Associate the updated reports with the corresponding Facilities for easy access.

### Ticket 3: Provide an API endpoint to retrieve Agent details by custom id

#### Description:
To support the integration of custom Agent ids into other systems, it is necessary to provide an API endpoint that allows external systems to retrieve Agent details using the custom id as a reference.

#### Acceptance Criteria:
- Implement an API endpoint to retrieve Agent details based on the custom id.
- The API endpoint should return the relevant Agent's information, including custom id, name, contact details, and any other necessary metadata.
- The response should follow the agreed-upon API format and standards.
- Proper error handling should be implemented for cases where an Agent with the specified custom id is not found.

#### Effort Estimate: 3 hours


Implementation Details:

1. Define a new API endpoint route for retrieving Agent details by custom id.
2. Implement the necessary logic to query the database based on the custom id.
3. Return the Agent details in the desired format, including the custom id, name, contact details, and any other required metadata.
4. Handle errors gracefully, returning appropriate error responses when an Agent with the specified custom id is not found.
