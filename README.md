# Javascript-Style-Guide
Skcript's Javascript Style Guide. This repo is meant to be subjective, and has been created based on our personal learnings. It's heavily inspired by [AirBnb’s Javascript Style Guide](https://github.com/airbnb/javascript). In fact, the below are modifications/additions to it. 

### Common
- Two spaces are used everywhere.
- Absolutely no console.logs in production.
- Don’t save references to this. Use bind if you are unable to access React's scope in a function.

```
// bad
function foo() {
  const self = this;
  return function () {
    console.log(self);
  };
}


// bad
function foo() {
  const that = this;
  return function () {
    console.log(that);
  };
}


// good
function foo() {
  return () => {
    console.log(this);
  };
}
```

- If the property/method is a boolean, use isVal() or hasVal()

```
// bad
if (!dragon.age()) {
  return false;
}


// good
if (!dragon.hasAge()) {
  return false;
}
```

- Do not add spaces inside brackets and curly braces.

```
// bad
const foo = [  1, 2, 3  ];
const foo = { clark: 'kent' };

// good
const foo = [1, 2, 3];
const foo = {clark: 'kent'};
```

### Variables

#### Naming Conventions
- Variables for values follow snake case.

```
var main_content;
var selected_image_id;
```

- Variables for functions follow camel case.

```
var showFiles = function showFiles(file) {
  // Logic...
}
```

- Keys defined in objects follow camel case.

```
var info = {
  companyName: "Skcript",
  officeLocation: "Chennai"
};
```

- Classnames follow pascal case.

```
var TaskShow = React.createClass({});
Prefix jQuery object variables with a $

// bad
const sidebar = $('.sidebar');


// good
const $sidebar = $('.sidebar');


// good
const $sidebarBtn = $('.sidebar-btn');
```

#### Good Practices
- All variables must be defined at the top of the function before using them.
- Assign default values for variables which require them.
- Define variables from external libraries first.
- Logically separate variable groups with new lines.
- Do no use reserved variable names.
- All variable definitions must end with a semicolon.

```
render: function() {
  var Modal = ReactBootstrap.Modal;
  let count = 0;
  let multiplier = 5;

  if (this.props.sample == 10) {
    count = multiplier x this.props.sample;
  }
}
```

- Objects are defined with their keys staring in a new line and then two spaces.

```
var info = {
  companyName: "Skcript",
  officeLocation: "Chennai"
};
```

#### Using var, const and let
- Use const for all of your references that do not change during the cycle.

**Why?** This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.

```
// bad
var a = 1;
var b = 2;


// good
const a = 1;
const b = 2;
```

- If you must reassign references, use let instead of var

**Why?** let is block-scoped rather than function-scoped like var.

```
// bad
var count = 1;
if (true) {
  count += 1;
}


// good, use the let.
let count = 1;
if (true) {
  count += 1;
}
```

_Note that both let and const are block-scoped._

```
// const and let only exist in the blocks they are defined in.
{
  let a = 1;
  const b = 1;
}
console.log(a); // ReferenceError
console.log(b); // ReferenceError
```

### React Component Variables
- Props passed to the component are each defined in a new line, with a two space indent.
- Closing tags for components end on the same line as the last prop.
- If there are less than 3 props, pass them along the same line.

```
// bad
  <UserThumbnail user={user} className="small" admin={true} color= "SpaceGray" />

// bad
<UserThumbnail
                                 user={user}
                                 className="small"
                                 admin={true}
                                 color= "SpaceGray"
/>

// bad
<UserThumbnail user={user}
                                 className="small"
                                 admin={true}
                                 color= "SpaceGray"
/>

// good
<UserThumbnail
  user={user}
  className="small"
  admin={true}
  color= "SpaceGray" />
```

### Functions
#### Naming Conventions
- Always use camelCase for function names.
- Avoid single letter names. Be descriptive with your naming.

#### Good Practices
- Each function must be atomic. I.E, must do only a single thing.
- All functions must be DRY in nature. (Avoid repetition)
- Add comments above the function name to describe it’s purpose.
- If functions are complex in nature, add comments within also.
- Map functions should generally be restricted to taking one parameter.
- Map functions should be named in plural case, and their parameter in the singular.

```
var showAssignees = function showAssignees(assignee) {
  return <li key={assignee.id}>{assignee.name}</li>;
}
```

#### Syntax
- Functions names are preceded with a `:` and the name function.

```
showDate: function()
```
- Single space is given after just before the `{` starts.

```
// bad
showDate: function(){
  // Logic
},

// good
showDate: function() {
  // Logic
},
```

### Conditionals
#### Good Practice
- Leave a blank line after blocks and before the next statement.

```
// bad
if (foo) {
  return bar;
}
return baz;


// good
if (foo) {
  return bar;
}


return baz;
```

- Do not pad your blocks with blank lines.

```
// bad
function bar() {


  console.log(foo);


}


// also bad
if (baz) {


  console.log(qux);
} else {
  console.log(foo);


}


// good
function bar() {
  console.log(foo);
}


// good
if (baz) {
  console.log(qux);
} else {
  console.log(foo);
}
```

#### Syntax
- Else statements immediately precede the if statements. On the same line.

```
// bad
if (baz) {
  console.log(qux);
}
else {
  console.log(foo);
}

// good
if (baz) {
  console.log(qux);
} else {
  console.log(foo);
}
```

- If comparing array length, more than once. Save the length to a variable.

```
// bad
if (this.props.users.length == 0) {
  console.log("0 users");
} else if (this.props.users.length == 1) {
  console.log("1 user");
} else {
  console.log(this.props.users.length + " users");
}

// good
var length = this.props.users.length;

if (length == 0) {
  console.log("0 users");
} else if (length == 1) {
  console.log("1 user");
} else {
  console.log(length + " users");
}
```
