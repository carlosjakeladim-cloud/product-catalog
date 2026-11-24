# Mini Product Catalog

## Guide Questions

1. **What is the difference between props and state?**
   Props are data passed from a parent component to a child, and they cannot be changed by the child. State is data that a component keeps and updates by itself, and changing it makes the component re-render.

2. **Why can a child component not modify the props it receives?**
   Props belong to the parent component. React uses one-way data flow so the data stays predictable and only the owner (the parent) can change it.


3. **How does the onAddToCart callback allow data to flow from child to parent?**
    The parent passes a function down as a prop. When the button is clicked, the child calls that function and gives it the product title. The function runs in the parent, so the parent receives the data and updates its state.


4. **Why is the key prop required when rendering a list with .map()?**
   React uses the key to identify each item in the list so it knows which ones changed, were added, or were removed. If a key is missing or duplicated, React shows warnings and may update the wrong item or render the list incorrectly.


5. **What does the children prop allow you to do that a normal prop does not?**
   It lets you put any JSX between the opening and closing tags of a component, like the "New" or "Sale" badge. A normal prop only passes a value through an attribute, so children makes the component more flexible.