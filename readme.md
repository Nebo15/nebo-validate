# Nebo Validate

Simple library for form validation.
 
## Triggered events

### For validated element ```<input>```
- `validate` - triggered each time validation is triggered on element;
- `valid` - triggered when field is valid;
- `invalid` - tiggered when fiels is invalid;
- `validation-skipped` - when validation wasn't neccecary for value of element (for example, when field is empty).

### For form that contains validated element ```<form>```
- `change` - each time one of validated fields containing it changes;
- `field_valid` - one of form fields became valid. You can run ```$form.isValid();``` to make sure that all fields are valid;
- `field_invalid` - one of form fields became invalid.

## Methods
- ```$el.validate()``` returns $el - start validating for ```$el``` element;
- ```$elOrForm.isValid()``` returns boolean - check validity field or all fields of form;
- ```$form.getFirstInvalid()``` returns $el or false - returns first inalid element of form;
Also you can run validation by triggering event ```validate``` on form or it's element. Example: ```$('form').trigger('validate')```.

### Available rules
All rules are placed inside form html. Example: 
````
<input class="input" placeholder="**** **** **** ****" name="pan" type="text" data-validate-rule="card-number" required pattern="\d*" data-validate-filter="[\s\-]*" minlength="16" maxlength="19" autocomplete="cc-number" x-autocompletetype="cc-number" inputmode="numeric" id="cardNumber">
````

#### All fields
- required
- pattern
- fixLength
- data-validate-rule - when it's set to ```card-number``` validator would run Luhn checking
- data-validate-filter - rexept to filter validated data, for example when you use jQuery.mask plugin;

#### Input type number
- min
- max

#### Input type text
- minLength
- maxLength

### Example 
````
    var $inputs = $('input');
     
    // You can set event on witch validation will trigger
    $inputs.validate('change');
    
    // After each validation we trigger `validate`, `valid` and `invalid` events for input, and `change`, `field_valid`, `field_invalid` for form that contains it.
    $inputs.on('valid', function() {
        var $this = $(this);
        $this.removeError();
    });

    // validation-skipped event skipped
    $inputs.on('validation-skipped', function() {
        $(this).removeError();
    });

    // invalid event
    $inputs.on('invalid', function(event, rules_failed, rules) {});
    
````
