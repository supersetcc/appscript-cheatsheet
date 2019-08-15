# Get Range and Values

## getSheetByName
```
SpreadsheetApp.getActiveSpreadsheet().getSheetByName("sheetName");
```

## Get Last Row and Column
```
// const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("sheetName");
sheet.getDataRange().getLastRow()
sheet.getDataRange().getLastColumn()
```

## Get Values by Iterating Range
```
function getConfigs() {
  const configSheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("sheetName");
  const lastRow = configSheet.getDataRange().getLastRow();
  const range = configSheet.getRange(1,1,lastRow,2);
  const rangeValues = range.getValues();
  var configs = {}
  for (var j = 0 ; j < lastRow - 1; j++){
    configs[rangeValues[j][0]] = rangeValues[j][1]
  };
}
```

## Create Custom Menu
```
function onOpen() {
  SpreadsheetApp.getUi() // Or DocumentApp or SlidesApp or FormApp.
      .createMenu('Custom Menu')
      .addItem('Open', 'customFunction')
      .addToUi();
}
```

# Managing triggers programmatically
```
function createTimeDrivenTriggers() {
  // Trigger every 6 hours.
  ScriptApp.newTrigger('myFunction')
      .timeBased()
      .everyHours(6)
      .create();

  // Trigger every Monday at 09:00.
  ScriptApp.newTrigger('myFunction')
      .timeBased()
      .onWeekDay(ScriptApp.WeekDay.MONDAY)
      .atHour(9)
      .create();
}
```

