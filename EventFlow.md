# Event FLow


## Use Case 1: Check your library games approximate length (NoLogin)

**Primary Actor:** Anonymus user
**Secondary Actor:** System
**Preconditions**
-Has all the required software needed for the usage of the app installed

### Main Flow:
1. User presses the HowLongToBeat button.
2. New page appears asking for Steam ID
3. User inputs any valid Steam ID
4. System verifies the validity of the steam ID
  -If verification fails, system goes back to step 2
  -If verification succeeds a new page appears with all his library steam games ordered by game length with the data from the game length provided on the side.
5. If the user clicks onto the store button to the side of the games name, it takes them to the online steam shop page of the game

### Alternative Flows:
**A1: Non public games**
- If the inputted Steam ID has the games privacy settings not set as public:
1. The interface shows an error message with an Accept button in the center bottom.
2. User clicks the button.
3. Interface returns to step 2

**A2: Regret**
- If during step 2 the user wants to return to step 1:
1. User presses the arrow to the left button in the top left of the interface
2. System returns to the first interface(Step 1).


## Use Case 2: Log In/Out

**Primary Actor:** Anonymous user
**Secondary Actor:** System
**Preconditions**
-Has all the required software needed for the usage of the app installed

### Main Flow:
1. If not logged, user presses the "Log In" button (Should be possitioned in the top right corner).
2. New page appears asking for Steam login information.
3. User inputs any valid Steam login information.
  -If verificaton fails, system goes back to step 2.
  -If verification succeeds, the options that require logging in are unlocked and the system stores (just during the execution on a temporal registry) the login information for future uses.
4. The text of the button changes to "Log Out"

### Alternative Flows:

**A1: Regret**
- If during step 2 the user wants to return to step 1:
1. User presses the arrow to the left button in the top left of the interface
2. System returns to the first interface(Step 1).
**A2: Log out**
- If logged in:
1. User presses "Log Out" button (The same button of Log In with the text changed).
2. The main page is displayed.


## Use Case 3: Check your library games approximate length (LoggedIn)


**Primary Actor:** Identified user
**Secondary Actor:** System
**Preconditions**
-Has all the required software needed for the usage of the app installed
-Is logged in

### Main Flow:


1. User presses the HowLongToBeat button.
2. System inputs the users Steam ID to the HowLongToBeat input receiver. 
3. Since the login was successful to begin with there shouldnt be any issues with it, but:
  - If verification is rejected system sends user back to first interface and notifies of the error
  - If verification succeeds a new page appears with all his library steam games ordered by game length with the data from the game length provided on the side.
4.1. If the user clicks in the title of any of the games it opens the steam library on the games site(If we manage to configure that via steamcmd)
4.2. If the user clicks on the store button to the side of the games name, it takes them to the online steam shop page of the game

### Alternative Flows:

**A1: Regret**
- If during step 4 the user wants to return to step 1:
1. User presses the arrow to the left button in the top left of the interface
2. System returns to the first interface(Step 1).

## Use Case 4: Recommend games depending on either games you have played the most or games you have played the most reciently (LoggedIn)


**Primary Actor:** Identified user
**Secondary Actor:** System
**Preconditions**
-Has all the required software needed for the usage of the app installed
-Is logged in


### Main Flow:


1. User presses the recommend games button(will be locked until login)
2. System shows a combo box with two options (games from inside the library and games from outside the library) and 2 radio buttons (games you have played the most in your lifetime or games you have played the most recently).
3. User selects their preffered configuration and press the select button in the center bottom of the pane.
4. System returns a list with the recommended games depending on:
  - Combo box:
  - If the user only selects the games from inside the library configuration it limits the access to the games that are already known to be inside the library.
  - If the user only selects the games from outside the library configuration it receives chunks of recommended games from the whole database and excludes any game that is already in their library.
  - If the user selects both, it receives chunks of recommended games from the whole database.
  -
  - Radio button:
  - If the user selects games you have played the most in your life, it selects the genres of the 20 games with most hour play time and gives them an attribute of priority that will signify how relevant this genre is (the attribute will be calculated by squared_root(hours_played))
  - If the user selects games you have played the most recently, it selects the genres of the 20 games with most hour play time during the last two weeks (if no play time in the last two weeks it adds two weeks untilk there is relevant information) and 
    gives them an attribute of priority that will signify how relevant this genre is (the attribute will be calculated by squared_root(hours_played)).
5.1. If the user clicks in the title of any of the games it opens the steam library on the games site(If we manage to configure that via steamcmd and the game is inside the library)
5.2. If the user clicks on the store button to the side of the games name, it takes them to the online steam shop page of the game

### Alternative Flows:
**A1: Further filtering**
- The system interface that appears after the 4th step has a "filter" button in the top left.If pressed:
1. The system shows a new small interface with more specific filters (selectable as combo boxes) that may limit either genres, non-discounted games or other miscellaneous options.
2.1 If any filter is selected and a Confirm button is selected the system brigns forth a new list that includes both previewsly defined filters (inside/outside library, etc) and new ones (genres, etc).
2.2 If the cancel button is selected it loads back the previous list.

**A2: Recommended by friends**
- In the 2nd step interface, there will be a button in the bottom of the page named "Recommendations from friends". If pressed:
2. The system makes a list of all the recommendations made by your friends. The list shows: 
  - The names of both the game and the friend who recommended it
  - Their reviews if they wrote any
  - A button with the shops link to the game
3.1 If the user clicks in the title of any of the games it opens the steam library on the games site(If we manage to configure that via steamcmd and the game is inside the library)
3.2 If the user clicks on the store button to the side of the games name, it takes them to the online steam shop page of the game

**A3: Regret**
- If during step 2 the user wants to return to step 1:
1. User presses the arrow to the left button in the top left of the interface
2. System returns to the first interface(Step 1).

