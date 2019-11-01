function createPickEmForm() {
   // Create & name Form 
   var week = 1;  // Vary this to the select week
   var item = "NFL Week " + week + " Pick 'Em";  
   var form = FormApp.create(item)  
       .setTitle(item)
       .setDescription('') // Add a description if you want
       .setCollectEmail(true); // Has form require an email


   //Creates a single line text field  
   item = "Name";  
   form.addTextItem()  
       .setTitle(item)  
       .setRequired(true); // Reponse is required
  
  // Load Google Sheets file of 2019 NFL schedule
  // Headers are: Week Day Away Home
  var app = SpreadsheetApp;
  var sheet = app.openById(''); //Input the Google Sheets ID
  var sched = sheet.getRange('A2:D257').getValues(); // Adjust to grab select range.
  
  //Multiple Choice Items (Loop) 
  //Sunday Games
  var i;
  for (i = 0; i < sched.length; i++) {
    if (sched[i][1] == "Sun" && sched[i][0] == week)  //Creates item only if a Sunday Game for the select week 
    {
      item = sched[i][2] + " @ " + sched[i][3];  
      var away =  sched[i][2].split(" "); 
      var home = sched[i][3].split(" ");  
      var choices = [away[away.length - 1], home[home.length - 1]];  
      form.addMultipleChoiceItem()  
       .setTitle(item)  
       .setChoiceValues(choices)  
       .setRequired(true); 
  }
 }
  
  //Multiple Choice Items (Loop)
  //Monday Game(s)
  var i;
  for (i = 0; i < sched.length; i++) {
    if (sched[i][1] == "Mon" && sched[i][0] == week) //Creates item only if a Monday Game for the select week 
    {
      item = sched[i][2] + " @ " + sched[i][3];  
      var away =  sched[i][2].split(" "); 
      var home = sched[i][3].split(" ");  
      var choices = [away[away.length - 1], home[home.length - 1]];  
      form.addMultipleChoiceItem()  
       .setTitle(item)  
       .setHelpText('MONDAY NIGHT GAME')
       .setChoiceValues(choices)  
       .setRequired(true); 
  }
}
  
  //New Section
  //Tie Breaker
    var item = form.addSectionHeaderItem();
    item.setTitle('TIE BREAKER BELOW');
    item.setHelpText('CLOSEST TO ACTUAL SCORE WINS IT!'
                 + '\n \n *If this is also a tie, pot will be split.');

  //Add text item and requires it to be a number.
    item = 'Monday Night Game Combined Score?';
    var textItem = form.addTextItem()
                       .setTitle(item);
    var textValidation = FormApp.createTextValidation()
                                .requireNumber()
                                .build();
    textItem.setValidation(textValidation)
             .setRequired(true);
  }
