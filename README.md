# Angular21Tutorial


# Angular Events – Complete Guide with Examples

## 1. What are Events in Angular?

Events in Angular are actions performed by users or the browser that Angular can detect and respond to.

For example:

- Clicking a button.
- Typing something into an input field.
- Changing a dropdown selection.
- Moving the mouse over an element.
- Focusing or leaving an input field.

Angular uses event binding to handle these events.

### Event binding syntax

HTMLWrap linesCopy codePreview

```html
<element (eventName)="methodName()"></element>
```

Here:

- `(eventName)` – The event we want to listen to.
- `methodName()` – The component method that executes when the event occurs.

Example:

HTML:

HTMLWrap linesCopy codePreview

```html
<button (click)="showMessage()">
  Click Me
</button>
```

TypeScript:

typescript

```typescript
showMessage() {
  alert('Button Clicked!');
}
```

When the user clicks the button, Angular calls the `showMessage()` method.

## 2. Input Event vs Change Event

Both events are used to detect changes in input fields, but they work differently.

### A. Input Event

The `input` event triggers immediately whenever the user changes the input value.

Example:

HTML:

HTMLWrap linesCopy codePreview

```html
<input type="text" (input)="onInput()">

<p>You are typing...</p>
```

TypeScript:

typescript

```typescript
onInput() {
  console.log('Input event triggered');
}
```

If the user types `Angular`, the event triggers for each character.

Input event demonstration

\<input type="text" (change) = "handleEvent($event.type)\>

Input event simulation

Current value: \<input type="text" (change) = "handleEvent($event.type)\>

Event triggers: 56 character changes (in this demo).

### B. Change Event

The `change` event triggers when the value is committed.

For a text input, this generally happens when the user changes the value and then leaves the field.

Example:

HTML:

HTMLWrap linesCopy codePreview

```html
<input type="text" (change)="onChange()">
```

TypeScript:

typescript

```typescript
onChange() {
  console.log('Change event triggered');
}
```

For example:

1. User enters `Angular`.
2. User clicks outside the input.
3. Change event is triggered if the value changed.

### Difference between Input and Change

| Input Event | Change Event |
| --- | --- |
| Triggers as value changes | Triggers when change is committed |
| Usually fires on every edit | Usually fires once per committed change |
| Useful for live search | Useful for final value processing |

Real-world use cases:

- Input event: Live search, character counter, instant validation.
- Change event: Saving updated values, processing completed input.

## 3. Click Event on Button

The `click` event triggers whenever a user clicks an element.

HTML:

HTMLWrap linesCopy codePreview

```html
<button (click)="onClick()">
  Submit
</button>
```

TypeScript:

typescript

```typescript
onClick() {
  console.log('Button clicked');
}
```

### Passing a value with the click event

HTML:

HTMLWrap linesCopy codePreview

```html
<button (click)="showMessage('Hello Angular')">
  Click Me
</button>
```

TypeScript:

typescript

```typescript
showMessage(message: string) {
  console.log(message);
}
```

Output:

text

```text
Hello Angular
```

### Practical example: Counter

typescript

```typescript
count = 0;

increment() {
  this.count++;
}

decrement() {
  this.count--;
}
```

HTML:

HTMLWrap linesCopy codePreview

```html
<button (click)="increment()">+</button>

<h2>{{ count }}</h2>

<button (click)="decrement()">-</button>
```

Each click increases or decreases the counter.

Try the counter

# 0

− Decrease  \+ Increase  Reset

## 4. Select (Dropdown) Change Event

The `change` event is commonly used with dropdowns to detect which option the user selects.

HTML:

HTMLWrap linesCopy codePreview

```html
<select (change)="onCityChange($event)">
  <option value="">Select City</option>
  <option value="Mumbai">Mumbai</option>
  <option value="Pune">Pune</option>
  <option value="Delhi">Delhi</option>
</select>
```

TypeScript:

typescript

```typescript
onCityChange(event: Event) {
  const selectedCity =
    (event.target as HTMLSelectElement).value;

  console.log(selectedCity);
}
```

If the user selects Mumbai, the output is:

text

```text
Mumbai
```

### Practical example

typescript

```typescript
selectedCity = '';

onCityChange(event: Event) {
  this.selectedCity =
    (event.target as HTMLSelectElement).value;
}
```

HTML:

HTMLWrap linesCopy codePreview

```html
<select (change)="onCityChange($event)">
  <option value="">Select City</option>
  <option value="Mumbai">Mumbai</option>
  <option value="Pune">Pune</option>
  <option value="Delhi">Delhi</option>
</select>

<h3>Selected City: {{ selectedCity }}</h3>
```

## 5. Blur Event and Focus Event

These events are commonly used for form validation.

### A. Focus Event

The `focus` event triggers when an input field receives focus.

In simple words, when the user clicks inside an input field, the focus event occurs.

HTML:

HTMLWrap linesCopy codePreview

```html
<input
  type="text"
  (focus)="onFocus()"
>
```

TypeScript:

typescript

```typescript
onFocus() {
  console.log('Input field focused');
}
```

### B. Blur Event

The `blur` event triggers when an input field loses focus.

For example, when the user clicks outside the input field.

HTML:

HTMLWrap linesCopy codePreview

```html
<input
  type="text"
  (blur)="onBlur()"
>
```

TypeScript:

typescript

```typescript
onBlur() {
  console.log('Input field lost focus');
}
```

### Difference

| Focus Event | Blur Event |
| --- | --- |
| Element receives focus | Element loses focus |
| User enters the input | User leaves the input |
| Useful for showing hints | Useful for validation |

### Practical example

typescript

```typescript
message = '';

onFocus() {
  this.message = 'You are editing the input';
}

onBlur() {
  this.message = 'You left the input';
}
```

HTML:

HTMLWrap linesCopy codePreview

```html
<input
  type="text"
  (focus)="onFocus()"
  (blur)="onBlur()"
>

<p>{{ message }}</p>
```

## 6. Mouse Events (mouseenter and mouseleave)

Mouse events detect when the mouse pointer enters or leaves an element.

### A. Mouseenter Event

The `mouseenter` event triggers when the mouse pointer enters an element.

HTML:

HTMLWrap linesCopy codePreview

```html
<div (mouseenter)="onMouseEnter()">
  Move mouse here
</div>
```

TypeScript:

typescript

```typescript
onMouseEnter() {
  console.log('Mouse entered');
}
```

### B. Mouseleave Event

The `mouseleave` event triggers when the mouse pointer leaves an element.

HTML:

HTMLWrap linesCopy codePreview

```html
<div (mouseleave)="onMouseLeave()">
  Move mouse here
</div>
```

TypeScript:

typescript

```typescript
onMouseLeave() {
  console.log('Mouse left');
}
```

### Practical example

typescript

```typescript
message = 'Move your mouse over the box';

onMouseEnter() {
  this.message = 'Mouse entered the box';
}

onMouseLeave() {
  this.message = 'Mouse left the box';
}
```

HTML:

HTMLWrap linesCopy codePreview

```html
<div
  (mouseenter)="onMouseEnter()"
  (mouseleave)="onMouseLeave()"
>
  Hover Me
</div>

<p>{{ message }}</p>
```

Try mouse events

## Move or tap here

Interactive demonstration

Status: Outside the box

 Reset

## 7. How to Pass the $event Object in Angular?

This is one of the most important concepts in Angular event handling.

Angular provides a special variable called `$event`.

It contains information about the event that occurred.

For example:

- Which element triggered the event?
- What value was entered?
- Which keyboard key was pressed?
- What type of event occurred?

### Example 1: Input event

HTML:

HTMLWrap linesCopy codePreview

```html
<input
  type="text"
  (input)="getValue($event)"
>
```

TypeScript:

typescript

```typescript
getValue(event: Event) {
  const value =
    (event.target as HTMLInputElement).value;

  console.log(value);
}
```

If the user types `Hello`, the console displays the current input value.

### Example 2: Click event

HTML:

HTMLWrap linesCopy codePreview

```html
<button (click)="handleClick($event)">
  Click Me
</button>
```

TypeScript:

typescript

```typescript
handleClick(event: MouseEvent) {
  console.log(event);
  console.log(event.target);
  console.log(event.type);
}
```

Output:

text

```text
MouseEvent
button
click
```

### Example 3: Keyboard event

HTML:

HTMLWrap linesCopy codePreview

```html
<input
  type="text"
  (keyup)="onKeyUp($event)"
>
```

TypeScript:

typescript

```typescript
onKeyUp(event: KeyboardEvent) {
  console.log(event.key);
}
```

If the user presses A, output:

text

```text
a
```

### Important event object properties

| Property | Description |
| --- | --- |
| `event.target` | Element that triggered the event |
| `event.type` | Name of the event |
| `event.currentTarget` | Element whose listener is executing |
| `event.target.value` | Value of an input element (after appropriate typing) |
| `event.key` | Keyboard key pressed |
| `event.clientX` | Mouse X coordinate |
| `event.clientY` | Mouse Y coordinate |

Remember: `event.target` is typed as an `EventTarget`, so in TypeScript you often need to cast it to the appropriate HTML element.

## 8. How to Identify Which Event Is Triggered?

You can use the `event.type` property.

It tells you the name of the event that occurred.

HTML:

HTMLWrap linesCopy codePreview

```html
<button (click)="checkEvent($event)">
  Click
</button>

<input
  type="text"
  (input)="checkEvent($event)"
  (change)="checkEvent($event)"
  (focus)="checkEvent($event)"
  (blur)="checkEvent($event)"
>
```

TypeScript:

typescript

```typescript
checkEvent(event: Event) {
  console.log('Event Name:', event.type);
  console.log('Target Element:', event.target);
}
```

Possible console outputs:

text

```text
Event Name: click
Event Name: input
Event Name: change
Event Name: focus
Event Name: blur
```

This is a simple way to identify which event is triggered.

### More advanced example: Identify event using switch

typescript

```typescript
checkEvent(event: Event) {

  switch (event.type) {

    case 'click':
      console.log('Click event triggered');
      break;

    case 'input':
      console.log('Input event triggered');
      break;

    case 'change':
      console.log('Change event triggered');
      break;

    case 'focus':
      console.log('Focus event triggered');
      break;

    case 'blur':
      console.log('Blur event triggered');
      break;

    default:
      console.log('Unknown event');
  }
}
```

## 9. Angular Events Cheat Sheet

| Event | When it triggers |
| --- | --- |
| `(click)` | User clicks an element |
| `(dblclick)` | User double-clicks |
| `(input)` | Input value changes |
| `(change)` | Value change is committed |
| `(keyup)` | Keyboard key is released |
| `(keydown)` | Keyboard key is pressed |
| `(focus)` | Element receives focus |
| `(blur)` | Element loses focus |
| `(mouseenter)` | Mouse enters an element |
| `(mouseleave)` | Mouse leaves an element |
| `(mouseover)` | Mouse moves over an element |
| `(mouseout)` | Mouse moves out of an element |
| `(submit)` | Form is submitted |

## 10. Complete Practical Example

Let's combine multiple Angular events into one component.

app.component.ts

typescript

```typescript
export class AppComponent {

  name = '';
  selectedCity = '';
  message = '';

  onInput(event: Event) {
    this.name =
      (event.target as HTMLInputElement).value;
  }

  onClick() {
    this.message = 'Button clicked!';
  }

  onCityChange(event: Event) {
    this.selectedCity =
      (event.target as HTMLSelectElement).value;
  }

  onFocus() {
    this.message = 'Input focused';
  }

  onBlur() {
    this.message = 'Input blurred';
  }

  onMouseEnter() {
    this.message = 'Mouse entered';
  }

  onMouseLeave() {
    this.message = 'Mouse left';
  }
}
```

app.component.html

HTMLWrap linesCopy codePreview

```html
<h2>Angular Event Demo</h2>

<!-- Input Event -->
<input
  type="text"
  placeholder="Enter your name"
  (input)="onInput($event)"
  (focus)="onFocus()"
  (blur)="onBlur()"
>

<h3>Name: {{ name }}</h3>

<!-- Click Event -->
<button (click)="onClick()">
  Submit
</button>

<!-- Select Change Event -->
<select (change)="onCityChange($event)">
  <option value="">Select City</option>
  <option value="Mumbai">Mumbai</option>
  <option value="Pune">Pune</option>
  <option value="Delhi">Delhi</option>
</select>

<h3>City: {{ selectedCity }}</h3>

<!-- Mouse Events -->
<div
  (mouseenter)="onMouseEnter()"
  (mouseleave)="onMouseLeave()"
>
  Hover Me
</div>

<h3>{{ message }}</h3>
```

## 11. Important Interview Questions

Q1. What is event binding in Angular?

Event binding is used to listen to DOM events and execute component methods when an event occurs.

Q2. What is the difference between property binding and event binding?

- Property binding: Transfers data from component to HTML.
- Event binding: Transfers event notifications from HTML to component.

Q3. What is `$event` in Angular?

`$event` is a special variable that provides information about the event that occurred.

Q4. What is the difference between input and change events?

Input triggers during editing, whereas change triggers when the value is committed.

Q5. How do you get an input value using `$event`?

typescript

```typescript
getValue(event: Event) {
  console.log(
    (event.target as HTMLInputElement).value
  );
}
```

Q6. How do you identify which event is triggered?

Use:

typescript

```typescript
console.log(event.type);
```

Q7. What is the difference between mouseenter and mouseover?

- `mouseenter` does not bubble and triggers when entering the element.
- `mouseover` bubbles and can also trigger when entering child elements.
