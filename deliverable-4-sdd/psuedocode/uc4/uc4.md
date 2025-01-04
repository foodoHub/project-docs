```python
class MainNavigationController:
    def handleBottomNavigation(option):
        if option == "SocialFeed":
            showSocialFeed()
        elif option == "AIChat":
            showAIChat()
        elif option == "Profile":
            showProfile()

    def showSocialFeed():
        SocialFeedScreen.load()

    def showAIChat():
        AIChatScreen.load()

    def showProfile():
        ProfileScreen.load()
```