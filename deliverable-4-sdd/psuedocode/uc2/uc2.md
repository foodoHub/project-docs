```python
def handleRecoverPasswordFormSubmit(email):
    if validateEmail(email):
        sendResetLink(email)
        displayEnterCodeField()
    else:
        displayErrorMessage("Invalid email address")


def validateEmail(email):
    return Input.validateEmail(email)


def sendResetLink(email):
    ClerkSDK.sendResetLink(email)


def submitVerificationCode(code):
    response = ClerkSDK.verifyCode(code)
    if response["success"]:
        displayNewPasswordField()
    else:
        displayErrorMessage("Invalid verification code")


def submitNewPassword(newPass):
    response = ClerkSDK.updatePassword(newPass)
    if response["success"]:
        redirectToLoginPage()
    else:
        displayErrorMessage("Failed to update password")


def displayEnterCodeField():
    Input.showVerificationField()


def displayNewPasswordField():
    Input.showNewPasswordField()


def redirectToLoginPage():
    Navigation.toLoginPage()


def displayErrorMessage(message):
    Error.display(message)
```