var id =

'18IV3e_S9lp-7ReNr-yth7bM7QyAQtJS9Ot0ktG9_e5E';

var name = 'login';



function doGet(e) {

  var url = id;

  var sheetName = name;



  var myData = SpreadsheetApp.openById(id);

  var sheet = myData.getSheetByName(name);



  var json = convertSheet2Json(sheet);

  return ContentService.createTextOutput(JSON.stringify(json))

    .setMimeType(ContentService.MimeType.JSON);

}

function convertSheet2Json(sheet) {

  // first line(title)

  var firstRange = sheet.getRange(1, 1, 1, sheet.getLastColumn());

  var firstRowValues = firstRange.getValues();

  var titleColumns = firstRowValues[0];



  // after the second line(data)

  var lastRow = sheet.getLastRow();

  var rowValues = [];

  for(var rowIndex=2; rowIndex<=lastRow; rowIndex++) {

    var colStartIndex = 1;

    var rowNum = 1;

    var range = sheet.getRange(rowIndex, colStartIndex, rowNum, sheet.getLastColumn());

    var values = range.getValues();

    rowValues.push(values[0]);

  }



  // create json

  var jsonArray = [];

  for(var i=0; i<rowValues.length; i++) {

    var line = rowValues[i];

    var json = new Object();

    for(var j=0; j<titleColumns.length; j++) {

      json[titleColumns[j]] = line[j];

    }

    jsonArray.push(json);

  }

  return jsonArray;

}
