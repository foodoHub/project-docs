
```python
def handleEditPostFormSubmit(newCaption, newRecipe, newImageFile, postID):
    if validateInput(newCaption, newRecipe, newImageFile):
        imageUrl = None
        if newImageFile:
            imageUrl = uploadImage(newImageFile)
        updatedData = {
            "caption": newCaption,
            "recipe": newRecipe,
            "imageUrl": imageUrl
        }
        response = updatePost(updatedData, postID)
        if response["success"]:
            refreshFeed()
        else:
            displayErrorMessage(response["error_message"])
    else:
        displayErrorMessage("Invalid input data")

def validateInput(newCaption, newRecipe, newImageFile):
    return Input.validate(newCaption, newRecipe, newImageFile)

def uploadImage(newImageFile):
    signedUrl = PostService.getSignedURL()
    if signedUrl:
        success = ImageUploader.upload(newImageFile, signedUrl)
        if success:
            return signedUrl
    displayErrorMessage("Failed to upload image")
    return None

def updatePost(updatedData, postID):

    return PostService.updatePost(updatedData, postID)

def refreshFeed():
    SocialFeedScreen.refresh()

def displayErrorMessage(message):
    Error.display(message)
```