document.getElementById('registration-form').addEventListener('submit', function(event) {
    event.preventDefault();

    var password = document.getElementById('password').value;
    var confirmPassword = document.getElementById('confirmpassword').value;

    if (password !== confirmPassword) {
        alert('Passwords do not match');
    } else {
        alert('Registration successful');
    }
});