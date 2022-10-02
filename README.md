# Steel Eye

### 1. Explain what the simple `List` component does?
- Lists are used to display data in an ordered format and mainly used to display menus on websites. In react, List can be created in a similar way as we create lists in JavaScript. The map() function is used for traversing the lists. We use lists and keys to traverse the column element using map() code and will surround modifications in square brackets. The parts and components are then assigned  to listItems. 
- Finally, display this list on the web by putting the amount the `<ul>` and `</ul>` components. In order to create lists of pieces, students must use the character characteristic “key”, as specified in the React documentation. To determine whether items in a list had already been modified, added, or destroyed, React needed so many keys. An individual identifier is required for each object. The id about an entity usually works nicely for all of that. Whenever making lists of components in Java Script, users must use a special word attribute called “key”. React uses keys to indicate whether additional burdens have been modified, removed, or altered. Or, to put it another way, designers may say that keywords are applied to identify the components in collections.

### 2. What Problems / Warnings are there with code?

- The errors are found at line 52, and line 53 and also at the line 39
- At line 52 and 53 their was a error of shapeOf and propTypes.array is not a function. and map cannot read properties from items.


### 3. Please fix, optimize, and/or modify the component as much as you think is necessary?
 I think this can make the code run successfully

``` JavaScript
import React, { useState, useEffect, memo }from "react";
import PropTypes from "prop-types";
 
// Single List Item
const WrappedSingleListItem = ({ index, isSelected, onClickHandler, text }) => {
 return (
   <li
     style={{ backgroundColor: isSelected ? "green" : "red" }}
     onClick={onClickHandler(index)}
   >
     {text}
   </li>
 );
};
 
WrappedSingleListItem.propTypes = {
 index: PropTypes.number,
 isSelected: PropTypes.bool,
 onClickHandler: PropTypes.func.isRequired,
 text: PropTypes.string.isRequired
};
 
const SingleListItem = memo(WrappedSingleListItem);
 
// List Component
const WrappedListComponent = ({ items }) => {
 const [setSelectedIndex, selectedIndex] = useState();
 
 useEffect(() => {
   setSelectedIndex(null);
 }, [items]);
 
 const handleClick = (index) => {
   setSelectedIndex(index);
 };
 
 return (
   <ul style={{ textAlign: "left" }}>
     {items.map((item, index) => (
       <SingleListItem
         onClickHandler={() => handleClick(index)}
         text={item.text}
         index={index}
         isSelected={selectedIndex}
       />
     ))}
   </ul>
 );
};
 
WrappedListComponent.propTypes = {
 items: PropTypes.arrayOf(
   PropTypes.shape({
     text: PropTypes.string.isRequired
   })
 )
};
 
WrappedListComponent.defaultProps = {
 items: null
};
 
const List = memo(WrappedListComponent);
 
export default List;
 

```
