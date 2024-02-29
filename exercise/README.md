# ![React Router DOM Lab - Exercise](./assets/hero.png)

## Overview

![tktk Hunter - screenshots of app]()

In this lab, you will build an application that simulates a post office, where users can create new mailboxes, view a list of all mailboxes, and explore details about each mailbox. In completing this lab, you will utilize several client-side routing tools provided by `react-router-dom`.

Take a look at the component hierarchy diagram below for a sense of how this application will be structured:

![tktk Hunter](./assets/placeholder-chd.png) 

In the list below, you'll find a brief description of the role of each component in our app:

- **App**: The root component that orchestrates the entire application.
- **NavBar**: Provides navigation links.
- **MailboxForm**: Allows users to enter details for and submit new mailboxes.
- **MailboxList**: Displays an index list of all mailboxes.
- **MailboxDetails**: Shows details about a specific mailbox.

## User stories

Here are the user stories for this lab:

- As a user, I should see a nav bar with links at the top of each page in the application. 

- As a user, clicking on the 'Home' link should navigate me to a landing page that displays the text 'Post Office'. 

- As a user, clicking on the 'New Mailbox' link should navigate me to a page with a form for submitting new mailboxes. 

- As a user, when viewing the form on the 'New Mailbox' page, I should see a `<form>` with an `<input>` for the name of the `boxholder` and a `<select>` menu for the `boxsize`. The `<select>` menu should include three options: 'Small', 'Medium', and 'Large'.

- As a user, I should not be required to select a box number when creating a new mailbox. When a new mailbox is created, it should be assigned a box number, or `_id`, automatically. This number should increment based on the number of mailboxes that already exist. 

- As a user, when I submit a the 'New Mailbox' form, I should be redirected to the 'Mailboxes' page (`/mailboxes`) where I will see the newly created mailbox added to the list. 

- As a user, clicking on the 'Mailboxes' link should navigate me to a 'Mailboxes' page.

- As a user, when viewing the 'Mailboxes' page, I should be able to see a list of all the existing mailboxes. Each mailbox in the list should be a square container with a box number (`_id`).

- As a user, when viewing the 'Mailboxes' list page, I want to be able to click on a mailbox, and be directed to a mailbox details page.

- As a user, when viewing the details page, I should see details about a specific mailbox. The details should include the box number (`_id`), the name of the boxholder, and the box size. 

- As a user, I should see the message 'Mailbox Not Found!' if I navigate to the details page for a mailbox that does not exist.

## Lab exercise

Your primary goal is to implement the user stories listed above. To get started, you can follow the steps below:

1. Start by creating each of the components listed below. After creating each component, be sure to import them at the top of `src/App.jsx`.

    - `src/components/NavBar.jsx`
    - `src/components/MailboxForm.jsx`
    - `src/components/MailboxList.jsx`
    - `src/components/MailboxDetails.jsx`

2. Within `src/components/NavBar.jsx`, import `Link` from `react-router-dom` and create a `<Link>` for each destination in the table below:

    | Destination | `to`  | Text Content |
    | --- | --- | --- |
    | Home | `/` | Home |
    | MailboxList | `/mailboxes` |  Mailboxes |
    | MailboxForm | `/new-mailbox` |  New Mailbox |

3. In `src/App.jsx`, import `Route` and `Routes` from `react-router-dom` and create a `<Route>` for each destination in the table below:

    | Destination | `path` | `element` |
    | --- | --- | --- |
    | Home | `/` | `<main><h1>Post Office</h1></main>` | 
    | MailboxList | `/mailboxes` |  `<MailboxList />` |
    | MailboxForm | `/new-mailbox` | `<MailboxForm />` |
    | MailboxDetails | `/mailboxes/:mailboxId` | `<MailboxDetails />` |

4. In `src/App.jsx`, import `useState` from `react` and create a new `useState` variable called `mailboxes`. Set its initial state to an empty array (`[]`).

5. In `src/App.jsx`, build the scaffolding for a function called `addBox`. It should accept form data for a new mailbox and `setMailboxes` state accordingly.  

### Hints

1. The `mailboxes` `useState` variable will be used to store an array of objects, each object representing a mailbox. Each mailbox object should adhere to the shape outlined below:

    ```jsx
    const mailboxExample = {
      _id: 0, boxSize: 'Small', boxholder: 'Alex',
    };
    ```

2. New mailboxes should receive a box number or `_id` property automatically. A good place to handle this would be the `addBox` function in `src/App.jsx`. The value of the `_id` property can be derived from the current `length` of `mailboxes` state. This value can be added to the submitted form data before the object is set in state.

3. When building out `src/components/MailboxDetails.jsx`, the `useParams()` hook should be useful. You can use the value extracted from the URL params to `find()` a specific mailbox in `mailboxes` state. 

    ```jsx
    // src/components/MailboxDetails.jsx
      const { mailboxId } = useParams();
      const selectedBox = props.mailboxes.find((mailbox) => mailbox._id === Number(mailboxId));
    ```