# Lab 3: Mini Product Catalog

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


# Lab 4: Live Search and Filter

## Guide Questions

1. **Why do we use two separate states, searchText and debouncedSearch, instead of only one?**
   searchText updates on every keystroke so the input stays responsive. debouncedSearch only updates after the user stops typing for 300ms, so the filtering does not run on every keystroke.

2. **What would happen if the debounce effect did not return a cleanup function?**
   The old timers would not be cancelled. Every keystroke would still trigger an update after 300ms, so the list would update many times and the debounce would not work.

3. **What is the purpose of the dependency array? What happens if it is empty ([])? What happens if it is left out completely?**
   The dependency array tells React when to re-run the effect, which is only when one of the listed values changes. If it is empty, the effect runs only once after the first render. If it is left out, the effect runs after every render.

4. **Why should we avoid sorting the original products array directly?**
   sort() changes the array it is called on. Changing the original data can cause bugs and the original order could not be restored, so we sort a copy made with the spread operator.

5. **Is the filtered product list better stored in its own state, or calculated from existing state during rendering? Explain your choice.**
   It is better to calculate it during rendering. The filtered list can always be worked out from products, debouncedSearch, category, and sortOrder, so storing it in state would duplicate data and could get out of sync.