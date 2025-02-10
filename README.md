# MathsCaptcha
MathsCaptcha is a simple PHP Class for using captchas in php forms. It works by creating a simple maths task displayed as SVG. The correct answer is served as hashed value with the SVG and can be compared after form submition with user input by classown method.

## The class
    $captcha=new MathsCaptcha("+|-|x|:")  
The class-Constructor expects an optional maths operator for the Captcha.

## Methods
    MathsCaptcha::verify(input,hash)
Calculates the hashvalue from captcha input and compares it with given hash.

    $captcha->getCaptchaJson()
Returns json-String with svg in field "_captcha_svg" and hash in "_captcha_hash"

    $captcha->getCaptcha()
Echoes a complete HTML-Snippet with SVG-Captcha, hidden hash input named "_captcha_hash" and solution input named "_captcha_solution". Uses all following methods.

    $captcha->getResultHash()
Returns the captcha result hash

    $captcha->getMaths()
Returns the captcha task as plain letters.

    $captcha->getSVGMaths
Returns the captcha task as SVG

## Simple Code example
In your form:

    $captcha=new MathsCaptcha(); 
    $captcha->getCaptcha();

In your form validation:

    if($_REQUEST&&$_REQUEST["_captcha_solution"]&&$_REQUEST["_captcha_hash"]){
        if(MathsCaptcha::verify($_REQUEST["_captcha_solution"],$_REQUEST["_captcha_hash"])){
        //PROCESS FORM
        }
    }
