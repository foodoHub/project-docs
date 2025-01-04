```python
def handleDeletePostButtonClick(postID):
    response = deletePost(postID)
    if response["success"]:
        refreshFeed()
    else:
        displayErrorMessage(response["error_message"])

def deletePost(postID):
    return PostService.deletePost(postID)

def refreshFeed():
    SocialFeedScreen.refresh()

def displayErrorMessage(message):
    Error.display(message)
```