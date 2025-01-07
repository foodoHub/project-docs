```python
def sendMessage(message, chatID):
    try:
        ChatController.createMessage(message, chatID)
        ChatScreen.updateChatList()
    except Exception as e:
        ChatScreen.displayErrorMessage(e)

class ChatController:
    def createMessage(message, chatID):
        ChatService.createMessage(message, chatID)

    def getChatHistory(chatID):
        return ChatService.getHistory(chatID)

class ChatService:
    def createMessage(message, chatID):
        ChatRepository.saveMessage(chatID, message)
        history = ChatRepository.getHistory(chatID)
        preferences = UserService.getUserPreferences(chatID)
        mealSuggestion = LLMProvider.getMealSuggestion(history, preferences)
        filteredSuggestion = VectorDBHandler.filterData(mealSuggestion)
        ChatScreen.displayAIResponse(filteredSuggestion)

    def getHistory(chatID):
        return ChatRepository.getHistory(chatID)

class ChatRepository:
    def saveMessage(chatID, message):
        database.saveMessage(chatID,message)

    def getHistory(chatID):
        return history

class UserService:
    def getUserPreferences(chatID):
        return preferences

class LLMProvider:
    def getMealSuggestion(history, preferences):
        # Logic to get meal suggestions from LLM
        return mealSuggestion

class VectorDBHandler:
    def filterData(mealSuggestion):
        # Logic to filter the meal suggestions
        return filteredSuggestion

def displayAIResponse(response):
    UI.showResponse(response)

def displayErrorMessage(message):
    UI.showError(msg)
```