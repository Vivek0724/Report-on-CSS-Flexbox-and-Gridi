# Report on CSS Flexbox and Grid with Code Samples

## CSS FLEXBOX
Flexbox is a layout mode in CSS3. It’s a more proficient approach to designing, aligning, and disseminating space between items in a container to control their arrangement.
With Flexbox, we can arrange items left to right, right to left, top to bottom, or bottom to top and, at the same time, control the spacing, alignment, and order of items in the container. 

## You should consider using Flexbox when:
**You have a small design to implement** Flexbox is ideal when you have a small layout design to implement, with a few rows or a few columns.
**You need to align elements** Flexbox is perfect for that, the only thing we should do is create a flex container using display: flex and then define the flex-direction that we want.                                                                                                                                             
**You need a content-first design** Flexbox is the ideal layout system to create web pages if you don’t know exactly how your content is going to look, so if you want everything just to fit in, Flexbox is perfect for that.

Of course, you can build your whole application using only Flexbox and get the same result as if you were building with CSS grid, that’s totally fine. But for a better CSS approach, to have a more concise, well-written, and maintainable application in the long-term, to create and fit your layout perfectly, the ideal method is to use CSS grid.

## Stretch all, fixed spacing
   
The most basic flexbox pattern: getting a few boxes to stretch and fill the full width of their parent element. All you need to do is to set display: flex on the container, and a flex-grow value above 0 on the children:

```
.container {
  display: flex;
}

.item {
  flex-grow: 1;
  height: 100px;
}

.item + .item {
  margin-left: 2%;
}

```

> We use a + selector to only add gaps between pairs of items (essentially just skipping the left margin for the first item in the list).

Increasing flex-grow will increase the amount of space that an element is allowed to stretch to compared to any other element. If we set flex-growto 2 on the middle element here, we would basically divide up the available space into 6 chunks (1 chunk for each item plus 1 extra for the middle item, 1+1+2+1+1). The middle item gets two chunks (flex-grow: 2) worth of space, and all other elements get one chunk (flex-grow: 1).

## Stretch middle, fixed spacing

A common app and web pattern is to create a top bar where we want to stretch only the middle element, but keep the right most and left most elements fixed. If we just want one element to stretch, we can set a fixed width (e.g. 100px) on an element that should stay static, and flex-grow: 1 on the element that should stretch:

```
.container {
  display: flex;
}

.item {
  height: 100px;
  width: 100px; /* A fixed width as the default */
}

.item-center { 
  flex-grow: 1; /* Set the middle element to grow and stretch */
}

.item + .item { 
  margin-left: 2%; 
}

```
> Even if the middle element here has a defined width of 100px, flex-grow will make it stretch to take up all the available space.

## 3*3 Grid
We can create a 3x3 grid by setting flex-grow to 0 and flex-basis to the preferred width for all children (here done using the flex short-hand: flex: 0 32%). The margins between the items are the leftovers from every row, i.e. (100%-32x3)/2=2%. I’ve matched the margin (margin-bottom: 2%) to achieve even spacing between all elements:

```
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.item {
  flex: 0 32%;
  height: 100px;
  margin-bottom: 2%; /* (100-32*3)/2 */
}

```
>You can change the flex-basis to increase or decrease the number of items on each row. flex: 0 24% would put 4 items on every row, flex: 0 19% would put 5 items on every row, and so on so forth

[common flexbox example](https://tobiasahlin.com/blog/common-flexbox-patterns/)

## GRID
CSS Grid Layout, is a two-dimensional grid-based layout system with rows and columns, making it easier to design web pages without having to use floats and positioning. Like tables, grid layout allow us to align elements into columns and rows.
To get started you have to define a container element as a grid with display: grid, set the column and row sizes with grid-template-columns and grid-template-rows, and then place its child elements into the grid with grid-column and grid-row.

## Important Terminology of Grid 
   
**Grid Container**
The element on which display: grid is applied. It’s the direct parent of all the grid items. In this example container is the grid container.

```
<div class="container">
  <div class="item item-1"> </div>
  <div class="item item-2"> </div>
  <div class="item item-3"> </div>
</div>

```
**Grid Item** 
The children (i.e. direct descendants) of the grid container. Here the item elements are grid items, but sub-item isn’t.
```
<div class="container">
  <div class="item"> </div>
  <div class="item">
    <p class="sub-item"> </p>
  </div>
  <div class="item"> </div>
</div>
```
**Grid Line**
      The dividing lines that make up the structure of the grid. They can be either vertical (“column grid lines”) or horizontal (“row grid lines”) and reside on either side of a row or column. Here the yellow line is an example of a column grid line.

[grid line](https://css-tricks.com/wp-content/uploads/2018/11/terms-grid-line.svg/gridline.png)

**Grid Cell**  
The space between two adjacent row and two adjacent column grid lines. It’s a single “unit” of the grid. Here’s the grid cell between row grid lines 1 and 2, and column grid lines 2 and 3.

**Grid Track**
The space between two adjacent grid lines. You can think of them as the columns or rows of the grid. Here’s the grid track between the second and third-row grid lines.

## CSS grid is better when:
**You have a complex design to implement**   in some use cases, we have complex designs to implement, and that’s when the magic of CSS grid shows itself. The two-dimensional layout system here is perfect to create a complex design, we can use it in our favor to create more complex and maintainable web pages
** You need to have a gap between block elements**    another thing that’s very helpful in CSS grid, that we don’t have in Flexbox, is the gap property. We can define the gap between our rows or columns very easily, without having to use the margin property, which can cause some side effects especially if we’re working with many breakpoints
** You need to overlap elements**    overlap elements using CSS grid is very easy, you just need to use the grid-column and grid-row properties and you can have overlapping elements very easily. On the other hand, with Flexbox we still need to use some hacks such as margins, transforms, or absolute positioning
** You need a layout-first design**   when you already have your layout design structure, it’s easier to build with CSS grid, and the two-dimensional layout system helps us a lot when we’re able to use rows and columns together, and position the elements the way we want


## UNIQUENESS IN GRID AND FLEXBOX:

**One Vs Two Dimension:**
- Grid is made for two-dimensional layout while Flexbox is for one. This means Flexbox can work on either row or columns at a time, but Grids can work on both.
- Flexbox, gives you more flexibility while working on either element (row or column). HTML markup and CSS will be easy to manage in this type of scenario.

**Content-First vs Layout-First:**
- Major Uniqueness between Flexbox and Grids is that the former works on content while the latter is based on the layout.
- The Flexbox layout is best suited to application components and small-scale layouts, while the Grid layout is designed for larger-scale layouts that are not linear in design. 
## DIFFERENCE BETWEEN GRID AND FLEXBOX :
     
**1. Dimensionality and Flexibility :**
- Flexbox offers greater control over alignment and space distribution between items. Being one-dimensional, Flexbox only deals with either columns or rows.
- Grid has two-dimension layout capabilities which allow flexible widths as a unit of length. This compensates for the limitations in Flex.

**2. Aligenment:**
- Flex Direction allows developers to align elements vertically or horizontally, which is used when developers create and reverse rows or columns.
- CSS Grid deploys fractional measure units for grid fluidity and auto-keyword functionality to automatically adjust columns or rows.

**3. Item Management:**
- Flex Container is the parent element while Flex Item represents the children. The Flex Container can ensure balanced representation by adjusting item dimensions. This allows developers to design for fluctuating screen sizes.
- Grid supports both implicit and explicit content placement. Its inbuilt automation allows it to automatically extend line items and copy values into the new creation from the preceding item.

|PROPERTY  |GRID  |FLEXBOX|
|---  |---  |---|
|Dimension  |Two-Dimensional  |One-Dimensional|
|Features  |Can flex combination of items through space-occupying Features  |Can push content element to extreme alignment|
|Support type  |Layout first  |content first|

.
 
## FLEXGRID.CSS CODE :

```
row {
    display: flex;
    width: 100%;
    flex-flow: row;
    flex-direction:row; 
    flex-wrap: wrap;
    justify-content: space-around;
    box-sizing: border-box;
}

.col-12 {
    flex-basis: 100%;
    max-width: 100%;
}

.col-6 {
    flex-basis: 50%;
    max-width: 50%;
}

.col-4 {
    flex-basis: 33%;
    max-width: 33%;
}

.col-4 {
    flex-basis: 33%;
    max-width: 33%;
}


.col-1 {
    flex-basis: 8.33%;
    max-width: 8.33%;
} 
```

![Flex-Grid](https://raw.githubusercontent.com/ritwickdey/sample-css-flex-grid/master/img/Flex-Grid.png)

## CONCLUSION 
   
- CSS Grids helps you create the outer layout of the webpage. You can build complex as well responsive design with this. This is why it is called ‘layout first’.
- Flexbox mostly helps align content & move blocks.
- CSS grids are for 2D layouts. It works with both rows and columns.
- Flexbox works better in one dimension only (either rows OR columns).
- It will be more time saving and helpful if you use both at the same time.

**REFERENCE LINKS 
  
- [Basic concepts of flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
 
- [complete guide grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
