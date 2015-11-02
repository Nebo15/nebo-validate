# Nebo Validate

Simple library for form validation.
 
### Example 
````
    var $inputs = $('input');
     
    // validate inputs on change event 
    $inputs.validate('change');
    
    // valid event callback
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
