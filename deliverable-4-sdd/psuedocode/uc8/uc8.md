```python
def displayFeed():
    try:
        initUI()
        postEntities = getAllPosts()
        postDTOs = mapEntitiesToDTOs(postEntities)
        renderPosts(postDTOs)
    except Exception as e:
        displayErrorMessage(str(e))

def initUI():
    SocialFeedScreen.initUI()

def getAllPosts():
    return PostService.getAllPosts()

def mapEntitiesToDTOs(postEntities):
    return [mapEntityToDTO(entity) for entity in postEntities]

def renderPosts(postList):
    SocialFeedScreen.renderPosts(postList)

def displayErrorMessage(message):
    Error.display(message)
```