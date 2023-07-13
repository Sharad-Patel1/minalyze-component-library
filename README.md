# minalyze-component-library
---

## Project setup
```
npm install @minalyze_ab/minalyze-component-library
```

# Usage
---

## Alert

#### Props
```js
/**
 * @param [String] alertType [information, success, error, warning, default(information)]
 * @param [String] title [Title for the alert]
 * @param [Function] onClose [What the alert does onClose]
 * @param [String] closeLabel [The button pressed to trigger the closeFunction default("Dismiss"), user will also have a "X" on top left to close/ignore]   
 */
```

#### Example
```html
    <MclAlert alertType="information" title="Title" :onClose='someCloseFunc()' >Example Alert</MclAlert>
    <MclAlert alertType="success" title="Title">This is a long Example Alert to show you what it can do.</MclAlert>
    <MclAlert alertType="error" title="Title">Example Alert</MclAlert>
    <MclAlert alertType="warning" title="Title">Example Alert</MclAlert>
```
## Box

#### Props
```js
/**
 * @param [String] title [Title for the box, REQUIRED]
 * @param [Boolean] isDark [Toggle light and dark on component]
 * @param [Boolean] isSelected [Toggle the select view]
 * @param [String] tag [blue, violet, orange, purple, green, default(blue)]
 */
```
#### Example
```html
    <MclBox title="Minalyze" :isDark="false" tag="blue" :isSelected="false" />
    <MclBox title="Minalyze" :isDark="true" tag="blue" :isSelected="true" />
    <MclBox title="Minalyze" :isDark="false" tag="blue" :isSelected="true" />
    
    <MclBox title="Minalyze" :isDark="false" tag="violet" :isSelected="false" />
    <MclBox title="Minalyze" :isDark="true" tag="violet" :isSelected="true" />
    <MclBox title="Minalyze" :isDark="false" tag="violet" :isSelected="true" />
    
    <MclBox title="Minalyze" :isDark="false" tag="orange" :isSelected="false" />
    <MclBox title="Minalyze" :isDark="true" tag="orange" :isSelected="true" />
    <MclBox title="Minalyze" :isDark="false" tag="orange" :isSelected="true" />
    
    <MclBox title="Minalyze" :isDark="false" tag="purple" :isSelected="false" />
    <MclBox title="Minalyze" :isDark="true" tag="purple" :isSelected="true" />
    <MclBox title="Minalyze" :isDark="false" tag="purple" :isSelected="true" />
    
    <MclBox title="Minalyze" :isDark="false" tag="green" :isSelected="false" />
    <MclBox title="Minalyze" :isDark="true" tag="green" :isSelected="true" />
    <MclBox title="Minalyze" :isDark="false" tag="green" :isSelected="true" />
```

## Button
#### Props
```js
/**
 * @param [Object] iconLeft [Pass in an icon to display on the left side]
 * @param [Object] iconRight [Pass in an icon to display on the right side]
 * @param [Boolean] isLoading [State, toggle the loading animation]
 * @param [Boolean] isDisabled [State, is the button Disabled, meaning block icon will appear on hover, and user will not be able to click on it]
 * @param [String] buttonType [primary, secondary, error, ghost, default(primary)] 
 */
```
#### Example
```html
    <MclButton buttonType="primary">New Button</MclButton>
    <MclButton buttonType="secondary">New Button</MclButton>
    <MclButton buttonType="error">New Button</MclButton>
    <MclButton buttonType="ghost">New Button</MclButton>

    <MclButton buttonType="primary" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
    <MclButton buttonType="secondary" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
    <MclButton buttonType="error" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
    <MclButton buttonType="ghost" :isLoading="loading" @click="loading = !loading">New Button</MclButton>
    
    <MclButton buttonType="primary" :disabled="true">New Button</MclButton>
    <MclButton buttonType="secondary" :disabled="true">New Button</MclButton>
    <MclButton buttonType="error" :disabled="true">New Button</MclButton>
    <MclButton buttonType="ghost" :disabled="true">New Button</MclButton>
```

## Input
#### Props
```js
/**
 * @param [String] placeholder [Placeholder text]
 * @param [Object] icon [add Icon to the Input]
 * @param [Boolean] isDark [State, Toggle light and dark on component]
 */
```
#### Example
```html
    <Mclinput placeholder="Email" v-model="emailAddress" :icon="emailIcon" :isDark="false" />
    <Mclinput placeholder="Password" v-model="pw" :icon="lock" :isDark="false" />
    <Mclinput placeholder="Email" v-model="emailAddress" :icon="emailIcon" :isDark="true" />
    <Mclinput placeholder="Password" v-model="pw" :icon="lock" :isDark="true" />
```

## Switch
#### Props
```js
/**
 * @param [Boolean] isDark [State, Toggle light and dark on component]
 * @param [Boolean] modelValue [Data to model]
 * @param [Boolean] highlighted [blue bg on toggle on default(true)]  
 */
```
#### Example
```html
    <McltoggleSwitch :highlighted="true" :isDark="false" />
    <McltoggleSwitch v-model="toggleState" :highlighted="true" :isDark="false" />
    <McltoggleSwitch :highlighted="true" :isDark="true" />
    <McltoggleSwitch v-model="toggleStateDark" :highlighted="true" :isDark="true" />
    <McltoggleSwitch :isDark="false" />
    <McltoggleSwitch v-model="toggleState" :isDark="false" />  
    <McltoggleSwitch :isDark="true" />
    <McltoggleSwitch v-model="toggleStateDark" :isDark="true" /> 
```




