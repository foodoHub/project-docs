```python
def handleCreatePostFormSubmit(caption, recipe, imageFile):
    if validateInput(caption, recipe, imageFile):
        imageUrl = None
        if imageFile:
            imageUrl = uploadImage(imageFile)
        postData = {"caption": caption, "recipe": recipe, "imageUrl": imageUrl}
        response = createPost(postData)
        if response["success"]:
            refreshFeed()
        else:
            displayErrorMessage(response["error_message"])
    else:
        displayErrorMessage("Invalid input data")

def validateInput(caption, recipe, imageFile):
    return Input.validate(caption, recipe, imageFile)

def uploadImage(imageFile):
    signedUrl = PostService.getSignedURL()
    if signedUrl:
        success = ImageUploader.upload(imageFile, signedUrl)
        if success:
            return signedUrl
    displayErrorMessage("Failed to upload image")
    return None

def createPost(postData):
    return PostService.createPost(postData)

def refreshFeed():
    SocialFeedScreen.refresh()

def displayErrorMessage(message):
    Error.display(message)

```