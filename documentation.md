# NLIS Protocol Overview
### v0.9.0

The Natural Language Interface Specification (NLIS) is a protocol designed to describe user interfaces in a simple, structured, and human-readable format. The primary goal of NLIS is to facilitate the communication between developers, designers, and AI systems during the design and development process of user interfaces.

The essence of NLIS is to provide a clear and concise representation of user interfaces by breaking them down into their essential components, such as layout, elements, and events. By focusing on high-level abstractions, NLIS allows for seamless collaboration between humans and AI, enabling the generation of code or visual mockups from the same specification.

NLIS is built on the mindset of simplicity, flexibility, and reusability. It encourages a modular approach to interface design, where complex interfaces can be composed of reusable components, each with its own NLIS specification. This approach promotes consistency and maintainability across projects while minimizing redundancy and complexity.

In the following sections, we will dive deeper into the specific aspects of the NLIS protocol, such as metadata, layout, elements, and events.

# Metadata

The Metadata section of the NLIS protocol provides essential information about the interface, such as its name, description, and unique identifier. This information helps give context to the interface and serves as a brief overview for developers, designers, and AI systems working with the specification.

Here's an example of the Metadata section in a simple NLIS document:

```markdown
metadata:
  id: UniqueIdentifier
  type: Screen
  name: User Login Interface
  description: A simple user login interface for a web application.
```



In this example, the Metadata section includes the following attributes:
- `id` (string): A unique identifier for the interface. This can be useful for referencing the interface within other NLIS specifications or managing a library of reusable components.
- `type` (string): The type of the interface, such as "Screen" for a complete user interface, or "Component" for a reusable UI component.
- `name` (string): A human-readable name for the interface, which can be used for documentation or communication purposes.
- `description` (string): A brief description of the interface's purpose and functionality, providing additional context and understanding for collaborators.

# Layout

The Layout section of the NLIS protocol defines the structure and arrangement of UI elements within the interface. Each UI element in the layout is represented by an object with specific attributes that describe its purpose, appearance, and functionality.

Here's an example of the Layout section in a simple NLIS document:

```markdown
layout:
  - type: Header
    description: A header with the application's logo and title.
    visual_description: A centered header containing the application's logo and title.
  - type: Form
    description: Login form with input fields for username and password, and a submit button.
    visual_description: A login form centered in the middle of the screen.
    elements:
      - type: Input
        description: Username input field.
        visual_description: A text input field with a label "Username".
      - type: Input
        description: Password input field.
        visual_description: A password input field with a label "Password".
      - type: Button
        description: Submit button.
        visual_description: A submit button with the label "Log In".
  - type: Footer
    description: A footer containing copyright information and useful links.
    visual_description: A simple footer placed at the bottom of the screen.
```



In this example, the Layout section contains a list of UI elements, each with the following attributes:
- `type` (string): The type of the UI element, such as "Header", "Form", or "Button".
- `description` (string): A brief description of the element's purpose and functionality.
- `visual_description` (string): A textual description of the element's appearance, providing a high-level understanding of its visual design.
- `elements` (array, optional): If the UI element contains other nested elements (e.g., a form containing input fields and a button), this attribute includes a list of those elements. The same structure applies to nested elements.

# Events

The Events section in the NLIS protocol describes the actions and interactions that occur within the interface. Events can include user interactions like clicking a button, submitting a form, or navigating between pages. Each event is represented by an object with specific attributes that describe its purpose and functionality.

Here's an example of the Events section in a simple NLIS document:

```markdown
events:
  - type: Event
    description: When the user clicks the "Log In" button, client-side validation is performed.
  - type: Event
    description: If the validation is successful, the form data is submitted to the server for further processing.
  - type: Event
    description: If server-side validation also passes, the user is redirected to the appropriate page.
  - type: Event
    description: In case of validation errors or other issues, an error message is displayed to the user.
```



In this example, the Events section contains a list of event objects, each with the following attributes:
- `type` (string): The type of the event, such as "Event".
- `description` (string): A brief description of the event's purpose and functionality.

By specifying the events in this manner, the NLIS protocol provides a clear and structured way to represent the interactive aspects of a user interface, which can then be used by developers or other AI models to generate appropriate code or designs.


### Example 1
Here's a simple NLIS specification in YAML for a basic webpage with a header, main content, and a footer:


```markdown
metadata:
  id: SimplePage
  type: Screen
  name: Simple Web Page
  description: A simple webpage with a header, main content, and a footer.

layout:
  - type: Header
    description: A header containing the website logo and navigation menu.
    visual_description: A header with the website logo aligned to the left and a horizontal navigation menu.

  - type: MainContent
    description: The main content area of the webpage.
    visual_description: A responsive main content area that adjusts its width based on the screen size, displaying the main content of the page.

  - type: Footer
    description: A footer with copyright information and useful links.
    visual_description: A simple footer placed at the bottom of the screen, containing copyright information and useful links.

events:
  - type: Event
    description: When the user clicks a navigation link, the browser navigates to the corresponding page.
```

This example demonstrates the use of the NLIS protocol to specify a simple webpage layout, visual appearance, and user interaction events. The structure provided by NLIS allows for a clear and concise representation of the webpage, which can then be used to generate the actual design or code.


### Example 2
Here's an example of a simple NLIS specification for a "Call to Action" (CTA) button component and a webpage that uses this component:


```markdown
# CTA Button Component
metadata:
  id: CTAButton
  type: Component
  name: Call to Action Button
  description: A simple call to action button with customizable text and link.

layout:
  - type: Button
    description: A call to action button with customizable text.
    visual_description: A large, attention-grabbing button with customizable text.

events:
  - type: Event
    description: When the user clicks the button, the browser navigates to the specified link.

```
#### Webpage with CTA Button Component

```markdown
metadata:
id: CTAWebpage
type: Screen
name: Webpage with Call to Action Button
description: A simple webpage with a header, main content, CTA button component, and a footer.

layout:
- type: Header
  description: A header containing the website logo and navigation menu.
  visual_description: A header with the website logo aligned to the left and a horizontal navigation menu.

- type: MainContent
  description: The main content area of the webpage.
  visual_description: A responsive main content area that adjusts its width based on the screen size, displaying the main content of the page.

- type: Component(id=CTAButton)
  description: Call to action button component.
  visual_description: A large, attention-grabbing call to action button, placed below the main content area.

- type: Footer
  description: A footer with copyright information and useful links.
  visual_description: A simple footer placed at the bottom of the screen, containing copyright information and useful links.

events:
- type: Event
  description: When the user clicks a navigation link, the browser navigates to the corresponding page.
- type: Event
  description: When the user clicks the CTA button, the browser navigates to the specified link.

```

In this example, a simple "Call to Action" button component is specified using the NLIS protocol, and then it is incorporated into a webpage layout. This demonstrates how components can be specified and reused within different webpage designs, making it easier to maintain consistency and reusability across a web application.
