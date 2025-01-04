```python
def handleRegisterFormSubmit(email, firstName, lastName, password):
    if validateInputs(email, firstName, lastName, password):
        response = registerUser(email, firstName, lastName, password)
        if response["success"]:
            redirectToUserOnboardingScreen()
        else:
            displayErrorMessage(response["error_message"])
    else:
        displayErrorMessage("Invalid input")


def validateInputs(email, firstName, lastName, password):
    return Input.validate(email, firstName, lastName, password)


def registerUser(email, firstName, lastName, password):
    return ClerkSDK.register(email, firstName, lastName, password)


def redirectToUserOnboardingScreen():
    Navigation.toOnboardingScreen()


def displayErrorMessage(message):
    Error.display(message)

```