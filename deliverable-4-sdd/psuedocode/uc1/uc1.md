```python
def handleLoginFormSubmit(email, password):
    if validateInput(email, password):
        response = authenticateUser(email, password)
        if response["success"]:
            storeToken(response["token"])
            redirectToFeed()
        else:
            displayErrorMessage(response["error_message"])
    else:
        displayErrorMessage("Invalid input")


def validateInput(email, password):
    Input.validate.(email,password)


def authenticateUser(email, password):
    Clerk.authentice(email, password)


def storeToken(token):
    # Save token securely
    TokenStorage.add(token)


def redirectToFeed():
    # Navigate to the feed
    

def displayErrorMessage(message):
    # Display error message
    Error.display(message)
```