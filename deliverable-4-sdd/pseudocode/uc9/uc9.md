```python
def displayProfile():
    try:
        user = getUser(userId)
        displayProfileInfo(user)
    except Exception as e:
        displayErrorMessage(str(e))

def getUser(userId):
    userDTO = ClerkSDK.getUser(userId)
    userModel = mapToUserModel(userDTO)  
    return userModel

def displayProfileInfo(user):
    ProfileScreen.displayProfileInfo(user)

def displayErrorMessage(message):
    ProfileScreen.displayErrorMessage(message)

def mapToUserModel(userDTO):
    return UserModel(
        id=userDTO.id,
        username=userDTO.username,
        firstName=userDTO.firstName,
        lastName=userDTO.lastName,
        imageUrl=userDTO.imageUrl
    )
```