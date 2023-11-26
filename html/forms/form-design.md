## Form Design Guidelines

Good form design can [significantly reduce form abandonment rates](https://baymard.com/blog/checkout-flow-average-form-fields)

It's common practice to wrap a label and its widget with a [`<li>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/li) element within a [`<ul>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul) or [`<ol>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol) list. [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) and [`<div>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div) elements are also commonly used. Lists are recommended for structuring multiple checkboxes or radio buttons. In addition to the [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) element, it's also common practice to use HTML titles (e.g. [h1](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements), [h2](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements)) and sectioning (e.g. [`<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section)) to structure complex forms.

You should also visually differentiate between different types of form controls. A button should look like a button. An input like an input. Make it easy for users to recognize the purpose of a form control. For example, If something looks like a link, clicking on it should open a new page, and not submit a form.

### Labels

Do you want to add a new form control to your form? Start by adding the label for the new field. This way, you don't forget to add it. Adding labels first also helps you to focus on the form's goals–what data do I need here? Once this is clear, you can focus on helping the user enter data and complete the form.

[Research shows](https://ai.googleblog.com/2014/07/simple-is-better-making-your-web-forms.html) that best practice is to [position the label above the form control](https://www.uxmatters.com/mt/archives/2006/07/label-placement-in-forms.php), so the user can scan a form quickly and see which label belongs to which form control. 
### Help users navigate forms

[Research shows](https://baymard.com/blog/avoid-multi-column-forms) that it's best to use only a single column. Users don't want to spend time searching where the next form control is. By using one column, there is only one direction to follow. The tab order should also follow the visual order. You can view the [source order in Chrome DevTools](https://developer.chrome.com/blog/new-in-devtools-92/#source-order).
### Help users interact with forms

To avoid accidental taps and clicks, and help users interact with your form, make your buttons big enough. The recommended [tap target size](https://web.dev/articles/accessible-tap-targets) of a button is at least 48px. You should also add enough spacing between form controls using the `margin` CSS property to help avoid accidental interactions.

The default size of form controls is too small to be really usable. You should increase the size by using `padding` and changing the default `font-size`.

### Show errors where they happen

To make it straightforward for users to find out which form control needs their attention, display error messages next to the form control they refer to. When displaying errors on form submission, make sure to navigate to the first invalid form control.

### Make it clear to users what data to enter

Make sure users understand how to enter valid data. Do they need to enter at least eight characters for a password? Tell them.

```html
<label for="password">Password (required)</label><input required minlength="8" type="password" id="password" name="password" aria-describedby="password-minlength"><span id="password-minlength">Enter at least eight characters</span>
```

```html
<label for="name">Name (required)</label><input name="name" id="name" required>
```

### Usability Considerations
[source](https://www.smashingmagazine.com/2011/11/extensive-guide-web-form-usability/)
Web forms should generally have these six components:

1. **Labels**  
    These tell users what the corresponding input fields mean.
2. **Input Fields**  
    Input fields enable users to provide feedback. They include text fields, password fields, check boxes, radio buttons, sliders and more.
3. **Actions**  
    These are links or buttons that, when pressed by the user, perform an action, such as submitting the form.
4. **Help**  
    This provides assistance on how to fill out the form.
5. **Messages**  
    Messages give feedback to the user based on their input. They can be positive (such as indicating that the form was submitted successfully) or negative (“The user name you have selected is already taken”).
6. **Validation**  
    These measures ensure that the data submitted by the user conforms to acceptable parameters.

Despite differences in layout, functionality and purpose, all forms have three main aspects

1. **Relationship**  
    Forms establish a relationship between the user and the organization.
2. **Conversation**  
    They establish a dialogue between the user and the organization.
3. **Appearance**  
    By the way they look, they establish a relationship and a conversation.

#### Relationship Guidelines

- **Relationships are based on trust**, so establishing trust in your form is critical. This can be achieved through the logo, imagery, color, typography and wording. The user will feel at ease knowing that the form comes from a sincere organization.
- **Every relationship has a goal**, be it love and happiness in a romantic relationship or financial gain in a business relationship. Ask yourself, what is the goal of your form?
- **Base the name of the form on its purpose.**. That name will inform users what the form is about and why they should fill it in.
- Just as in a relationship, **getting to know the other person** is essential. Get to know your users and always consider whether the questions you’re asking are appropriate and, if so, whether they are timely. This will instill a natural flow to your form.
- Knowing your users will also help you **choose appropriate language and remove superfluous text**. And it will help you craft an interface that balances your needs and the user’s.
- **Do not ask questions beyond the scope of the form**. In a relationship, you would become distrustful of someone who asked questions that were out of place. The same thing happens online. Consult with relevant stakeholders to see what information really is required.
- **Sudden changes in behavior or appearance** will make users edgy. Likewise, never introduce sudden changes between forms or between steps in a form.
- **Order the labels logically**, reflecting the natural flow of a conversation. For example, wouldn’t it be weird to ask someone their name only after having asked a number of other questions? More involved questions should come towards the end of the form.

#### Conversation Guidelines

- Avoid aggressive wording
- **Remove clutter** such as banners and unnecessary navigation that might distract users from filling out the form.
- **Order the labels logically**, reflecting the natural flow of a conversation. For example, wouldn’t it be weird to ask someone their name only after having asked a number of other questions? More involved questions should come towards the end of the form.
- **Group related information**, such as personal details. The flow from one set of questions to the next will better resemble a conversation.
-
#### Appearance Guidelines
##### Labels
* If the purpose of a label is simple to understand, such as to ask for a name or telephone number, then a word or two should suffice. But a phrase or sentence might be necessary to eliminate ambiguity.
* Sentence case is slightly easier  to follow grammatically than title case. Never use all caps, or else the form would look unprofessional and be difficult to scan
##### Input Fields
- Provide the appropriate type of input field based on what is being requested. Each type of input field has its own characteristics, which users are accustomed to.
##### Actions
Primary actions are links and buttons in a form that perform essential “final” functionality, such as “Save” and “Submit.” Secondary actions, such as “Back” and “Cancel,” enable users to retract data that they have entered
	- Use only primary actions where possible. If you must include secondary actions, give them less visual weight than primary actions.
- Avoid generic words such as “Submit” for actions, because they give the impression that the form itself is generic. Descriptive words and phrases, such as “Join LinkedIn,” are preferred.
##### Help
* Should never need to explain how to fill out a form - if it doesn't look like a form or it's too complicated to fill out, redesigning is the only option. Accompanying text should be used only where needed.
* Show help only where required - could show an icon next to input that the user can click if they need help for that field. Can also display help when a user clicks into a specific field.

##### Messages
* Error messages should be emphasized through color, prominence (typically at the top of the form or beside the error, large, font, or a combination of these.
* Success messages encourage user to continue filling out the form - should be prominent but not hinder user from continuing.

##### Validation
* Only use where needed - excessive validation frustrates users.
* Use smart defaults to make form completion faster and more accurate.