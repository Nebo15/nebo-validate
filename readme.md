# Nebo Validate

Simple library for form validation.
 
### Example 
````
    var $inputs = $('input');
     
    // validate inputs on change event 
    $inputs.validate('change');
    
    // Jump to next input when data is valid
    $inputs.on('valid', function() {
        var $this = $(this);
        $this.removeError();
    });

    // Remove errors for skipped fields
    $inputs.on('validation-skipped', function() {
        $(this).removeError();
    });

    // Validation errors
    $inputs.on('invalid', function(event, rules_failed, rules) {});
    
````
