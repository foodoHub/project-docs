```python
def sendMessage(message, chatID):
    try:
        ChatController.createMessage(message, chatID)
        ChatScreen.updateChatList()
    except Exception as e:
        ChatScreen.displayErrorMessage(e)

class ChatController:
    def createMessage(message, chatID):
        ChatService.handleMessage(message, chatID)

    def getChatHistory(chatID):
        return ChatService.getHistory(chatID)

class ChatService:
    def handleMessage(message, chatID):
        ChatRepository.saveMessage(chatID, message)
        history = ChatRepository.getHistory(chatID)
        preferences = UserService.getUserPreferences(chatID)

        # Determine intent
        intent = LLMProvider.determineIntent(message, history)
        if intent == "Recipe Instruction":
            result = LLMProvider.getRecipeInstruction(history)
        elif intent == "Meal Suggestion":
            result = LLMProvider.getMealSuggestion(history, preferences)
        elif intent == "Harmful":
            result = ContentModerator.checkContent(message)
        else:
            raise ValueError("Invalid intent")

        # Filter and display results
        filteredData = VectorDBHandler.filterData(result)
        ChatScreen.displayAIResponse(filteredData)

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
    def determineIntent(message, history):
        # Logic to determine user intent
        return intent

    def getRecipeInstruction(history):
        # Logic to get recipe instruction
        return recipeInstruction

    def getMealSuggestion(history, preferences):
        # Logic to get meal suggestions
        return mealSuggestion

class ContentModerator:
    def checkContent(message):
        # Logic to detect harmful content
        return moderationResult

class VectorDBHandler:
    def filterData(data):
        return filteredData

def displayAIResponse(response):
    UI.showResponse(response)

def displayErrorMessage(message):
    UI.showError(msg)
```