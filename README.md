Download Link: https://assignmentchef.com/product/solved-2110215prog-midterm-2
<br>



<h1>1. Instruction</h1>

<ul>

 <li>Create Java Project named “<strong>2110215_Midterm_Q2</strong>”.</li>

 <li>Copy all folders in <strong>“Q2.zip”</strong> to your project directory src folder.</li>

 <li>You are to implement the following classes (detail for each class is given in section 3 and 4)

  <ol>

   <li><strong>BaseCard           </strong>(package logic.card)</li>

   <li><strong>NumberCard </strong>          (package logic.card)</li>

   <li><strong>DrawTwoCard </strong>          (package logic.card)</li>

   <li><strong>GameLogicUtility       </strong>(package logic.utility)</li>

  </ol></li>

 <li>Make UML class diagram for classes in package logic, using ObjectAid or another UML generator program. Save its picture file in your logic.card folder.</li>

 <li>JUnit for testing is in package test.</li>

 <li><strong>To submit: </strong>

  <ul>

   <li><strong>go to src folder that you actually do the coding for this question. </strong></li>

   <li><strong>Zip this question’s src folder. Name it YOUR-ID_Q2.zip (for example, 6332112121_Q2.zip) </strong></li>

   <li><strong>Submit the zipped file as an assignment on MyCourseville. </strong></li>

  </ul></li>

</ul>

<strong> </strong>




<h1>2. Problem Statement: ONU</h1>




Figure 1 ONU Game logo

We create UNO-liked puzzle game called ONU. The basic rule is very similar to UNO, but ONU is a single player game. ONU’s win condition is that player has to empty his/her hand before the deck is out.

In every turn, the player has to play 1 card from his/her hand by discarding it to the discard pile. However, each card type can only be played if certain condition(s) is satisfied.   There are 2 types of cards in ONU.

<ul>

 <li>a “number” card which has a number and a color on it. A number card can be played when it has the same color or same number as the top card of the discard pile. There are number 1 to number 4 cards for each color, RED, BLUE, YELLOW, and GREEN (16 in totals) in the deck.</li>

 <li>The second type is a “draw-two” card which has a draw-symbol and color on them. A player who plays a draw-two card has to draw 2 cards from the deck (there is only one player in our game anyway). A draw-two card can only be played when it has the same color as the top card on the discard pile. There are 4 “draw-two” cards in the deck, one for each color.</li>

</ul>




The game will end when the player’s hand is out of cards or the deck is out of cards.
















<h1>4.Implementation Detail</h1>

The class package is summarized below.

<strong>* In the following class description, only details of IMPORTANT</strong><strong> fields and methods </strong>

<strong>are given. *</strong>

4.1 Package logic.card <strong>/* You must implement this package from scratch*/</strong>

4.1.1 class BaseCard <strong>/* You must implement this class from scratch*/ </strong>

This class is a base class for all kind of Cards. It contains all common elements which a card should have.

<em>Field </em>

<table width="600">

 <tbody>

  <tr>

   <td width="241"><strong>Name</strong></td>

   <td width="359"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="241">– CardColor color</td>

   <td width="359">Color of the card. CardColor is enum in the package logic.game.</td>

  </tr>

  <tr>

   <td width="241">– CardSymbol symbol</td>

   <td width="359">Symbol of the card. CardSymbol is enum in the package logic.game.</td>

  </tr>

 </tbody>

</table>

<em>Method </em>

<table width="600">

 <tbody>

  <tr>

   <td width="243"><strong>Name</strong></td>

   <td width="358"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="243">+ BaseCard(CardColor color)</td>

   <td width="358">This is the Constructor.Set color as one given in the parameter.</td>

  </tr>

  <tr>

   <td width="243">+ void play()</td>

   <td width="358">This method is called when the card is played. The results of actions are different for each type of Cards.</td>

  </tr>

  <tr>

   <td width="243">+ boolean ruleCheck()</td>

   <td width="358">This method returns true if the card can be played according to the rule and returns false when the card is illegal to play. The rules are different for each type of Cards.</td>

  </tr>

  <tr>

   <td width="243">+ getter-setter for all fields.</td>

   <td width="358"></td>

  </tr>

 </tbody>

</table>













<h2>4.1.2. class NumberCard /* You must implement this class from scratch*/</h2>

This class is a type of Card. The top card of the discard pile must have same color or the same symbol to make this card playable. Playing a number card will change the top card of the discard pile to this card but no special effect happens.

<em>Method </em>

<table width="600">

 <tbody>

  <tr>

   <td width="211"><strong>Name</strong></td>

   <td width="389"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="211">+ NumberCard(CardColor color, CardSymbol symbol)</td>

   <td width="389">This is the Constructor.Set the information of the super class.Set symbol as one given in the parameter.</td>

  </tr>

  <tr>

   <td width="211">+ void play()</td>

   <td width="389">Use method setTopCard in class GameLogic to set this card to the top of the discard pile.You can call the method by using<strong><em>GameLogic.getInstance().setTopCard(…..)</em></strong>.*You do not need to check for play legality.</td>

  </tr>

  <tr>

   <td width="211">+ boolean ruleCheck()</td>

   <td width="389">return true if the top card of the discard pile has the same color or same symbol as this card. Otherwise, return false. You can use <strong><em>GameLogic.getInstance().getTopCard() </em></strong>to get the top card of the discard pile.</td>

  </tr>

 </tbody>

</table>






















<h2>4.1.3. class DrawTwoCard/* You must implement this class from scratch */</h2>

This class is a type of Card. The top card of the discard pile must have same color to make this card playable. Playing draw-two card will change the top card of the discard pile to this card and the player has to draw 2 cards from the deck.

<em>Method </em>

<table width="631">

 <tbody>

  <tr>

   <td width="205"><strong>Name</strong></td>

   <td width="426"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="205">+ DrawTwoCard(CardColor color)</td>

   <td width="426">This is the Constructor.Set the information of the super class.Set symbol as <strong><em>CardSymbol.DRAW</em></strong>.</td>

  </tr>

  <tr>

   <td width="205">+ void play()</td>

   <td width="426">Use method setTopCard in class GameLogic to set this card to the top of the discard pile.Then, use method draw in class GameLogic to draw 2 cards by setting the parameter of the method as 2.You can call the methods by using<strong><em>GameLogic.getInstance().setTopCard(…..)</em></strong>. and<strong><em>GameLogic.getInstance().draw(…..) </em></strong>*You do not need to check for play legality.</td>

  </tr>

  <tr>

   <td width="205">+ boolean ruleCheck()</td>

   <td width="426">return true if the top card of the discard pile has the same color as this card. Otherwise, return false.You can use <strong><em>GameLogic.getInstance().getTopCard() </em></strong>to get the top card of the discard pile.</td>

  </tr>

 </tbody>

</table>




4.2 Package logic.game

4.2.1. class GameLogic <strong>/*ALREADY PROVIDED*/</strong>

This class is the main game system. This class provides cards in deck, hand and game rules.

The game will be run via this class.

4.2.2. enum CardColor <strong>/*ALREADY PROVIDED*/</strong>

This enum contains values of color in this game.

4.2.3. enum CardSymbol <strong>/*ALREADY PROVIDED*/</strong>

This enum contains values of symbol on the cards.




4.3 Package logic.utility <strong>/* You must implement this package from scratch*/</strong>

4.3.1 class GameLogicUtility <strong>/* You must implement this class from scratch */</strong>

This class contains a method which will be used in GameLogic. Note: This is not the proper design of classes structure but it is required for scoring.

<em>Method </em>

<table width="600">

 <tbody>

  <tr>

   <td width="158"><strong>Name</strong></td>

   <td width="442"><strong>Description</strong></td>

  </tr>

  <tr>

   <td width="158"><u>+ boolean drawRule()</u></td>

   <td width="442">This method checks all cards in <strong>ArrayList&lt;BaseCard&gt; hand</strong> fromGameLogic as follows•      Return false, if there is any legal card to play in hand.•      Return true, if there is no legal card in hand.  You can get the hand of the player by using <strong><em>GameLogic.getInstance().getHand()</em></strong>.</td>

  </tr>

 </tbody>

</table>










4.4 Package main

<h2>4.4.1 class Main /*ALREADY PROVIDED*/</h2>

This class is the main program. You don’t have to implement anything in this class. You can test the program by running this class.




4.5 Package test.grader  <strong>/*ALREADY PROVIDED*/</strong>

This package provides JUnit test for each of your class.

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<strong> </strong>

<h1>5.Finished Code Run Example</h1>




5.1. Start the game




5.2. Game play




5.3. Play number card




5.4. Play draw-two card




5.5. Draw a card by rule




5.6. Play illegal card




5.7. Input index out of bounds




5.8. Win the game (empty the hand)




5.10. Lose the game (empty the deck)







<h1>6.Score Criteria</h1>

The maximum score for the problem is 15 and will be rounded down to 5.

<strong>6.1 Implement Class BaseCard, which does not have complete functions, correctly = 3 points </strong>

<table width="277">

 <tbody>

  <tr>

   <td width="192"><strong>6.2 Class NumberCard: </strong></td>

   <td width="85"><strong>= 3.5 points </strong></td>

  </tr>

  <tr>

   <td width="192"><strong>     </strong>testConstructor</td>

   <td width="85">= 1 points</td>

  </tr>

  <tr>

   <td width="192">     testPlay</td>

   <td width="85">= 1 points</td>

  </tr>

  <tr>

   <td width="192">     testRuleCheck</td>

   <td width="85">= 1.5 points</td>

  </tr>

  <tr>

   <td width="192"><strong>6.3 Class DrawTwoCard: </strong></td>

   <td width="85"><strong>= 3.5 points </strong></td>

  </tr>

  <tr>

   <td width="192"><strong>     </strong>testConstructor</td>

   <td width="85">= 1 points</td>

  </tr>

  <tr>

   <td width="192">     testPlay</td>

   <td width="85">= 1.5 points</td>

  </tr>

  <tr>

   <td width="192">     testRuleCheck</td>

   <td width="85">= 1 points</td>

  </tr>

 </tbody>

</table>

<strong>6.4 Class GameLogicUtility: = 3 points </strong>

<strong>     </strong>testRuleCheck         = 3 points

<strong>6.5 UML = 2 points </strong>

<strong>      </strong>All classes in package logic are present (correct variables and methods) = 1 points

Inheritance and Abstract structures are correct                                               = 1 points


