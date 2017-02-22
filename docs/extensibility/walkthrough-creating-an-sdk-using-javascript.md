---
title: "Exemplarische Vorgehensweise: Erstellen einer SDK mit JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Erstellen einer SDK mit JavaScript
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erfahren, wie JavaScript verwenden, um eine einfache mathematische SDK als eine Visual Studio\-Erweiterung \(VSIX\) zu erstellen.  Die exemplarische Vorgehensweise ist in folgende Teile gegliedert:  
  
-   [Das SimpleMathVSIX SDK Erweiterungsprojekt erstellen](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Zum Erstellen einer Beispielapp verwendet das SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Für JavaScript ist es keine Klassenbibliotheksprojekttyp. In dieser exemplarischen Vorgehensweise wird die Beispieldatei arithmetic.js direkt im VSIX\-Projekt erstellt. In der Praxis wird empfohlen, dass Sie zuerst erstellen und testen die JavaScript\- und CSS\-Dateien als Windows Store\-Apps – z. B. durch Verwendung der **leere App** Vorlage – bevor Sie diese in ein VSIX\-Projekt einzufügen.  
  
## Vorbereitungsmaßnahmen  
 Um diese exemplarische Vorgehensweise ausführen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Das SimpleMathVSIX SDK Erweiterungsprojekt erstellen  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  In der Liste der Kategorien unter **Visual C\#\-**, auf **Erweiterbarkeit**, und wählen Sie dann die **VSIX\-Projekt** Vorlage.  
  
3.  In den **Namen** Text geben `SimpleMathVSIX` und wählen Sie die **OK** Schaltfläche.  
  
4.  Wenn die **Assistenten für Visual Studio** angezeigt wird, wählen Sie die **Weiter** auf die Schaltfläche der **Willkommen** Seite und klicken Sie dann auf **Seite 1 von 7**, wählen Sie die **Fertig stellen** Schaltfläche.  
  
     Obwohl die **Manifest\-Designer** wird geöffnet und wir halten in dieser exemplarischen Vorgehensweise einfacher durch direktes Ändern der Manifestdatei.  
  
5.  In **Projektmappen\-Explorer**, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **Anzeigecode**. Verwenden Sie diesen Code, um den vorhandenen Inhalt der Datei zu ersetzen.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?> <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011"> <Metadata> <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" /> <DisplayName>Simple Math</DisplayName> <Description>Does basic arithmetic calculations.</Description> </Metadata> <Installation Scope="Global" AllUsers="true"> <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" /> </Installation> <Dependencies> <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" /> </Dependencies> <Assets> <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" /> </Assets> </PackageManifest>  
    ```  
  
6.  In **Projektmappen\-Explorer**, öffnen Sie das Kontextmenü für das SimpleMathVSIX\-Projekt, und wählen Sie dann **Hinzufügen**, **Neues Element**.  
  
7.  In der **Daten** Kategorie wählen **XML\-Datei**, nennen Sie die Datei `SDKManifest.xml`, und wählen Sie die **Hinzufügen** Schaltfläche.  
  
8.  In **Projektmappen\-Explorer**, öffnen Sie das Kontextmenü für die SDKManifest.xml\-Datei, und wählen Sie dann **Öffnen** zum Anzeigen der Datei in die **XML\-Editor**.  
  
9. Fügen Sie den folgenden Code in die Datei SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?> <FileList DisplayName="Simple Math" MinVSVersion="14.0" AppliesTo="JavaScript+WindowsAppContainer" SupportsMultipleVersions="Error" MoreInfo="http://www.msdn.microsoft.com/"> <!-- JS --> <File Content="js\arithmetic.js" /> </FileList>  
  
    ```  
  
10. In **Projektmappen\-Explorer**, wählen Sie im Kontextmenü für die Datei SDKManifest.xml **Eigenschaften**.  
  
11. In der **Eigenschaften** legen die **Include in VSIX** \-Eigenschaft **True**.  
  
12. In **Projektmappen\-Explorer**, wählen Sie im Kontextmenü für das Projekt SimpleMathVSIX **Hinzufügen**, **neuen Ordner**, und nennen Sie den Ordner `Redist`.  
  
13. Fügen Sie die Unterordner unter dem Redist dieser Ordnerstruktur zu erstellen:  
  
     \\Redist\\CommonConfiguration\\Neutral\\SimpleMath\\js\\  
  
14. Wählen Sie im Kontextmenü für den Ordner \\js\\ **Hinzufügen**, **Neues Element**.  
  
15. Klicken Sie unter **Visual C\#\-Elemente**, wählen die **Web** Kategorie, und wählen Sie dann die **JavaScript\-Datei** Element. Nennen Sie die Datei `arithmetic.js`, und wählen Sie dann die **Hinzufügen** Schaltfläche.  
  
16. Fügen Sie den folgenden Code in arithmetic.js:  
  
    ```  
    (function (global) { "use strict"; global.Arithmetic = { add: function (firstNumber, secondNumber) { return firstNumber + secondNumber; }, subtract: function (firstNumber, secondNumber) { return firstNumber - secondNumber; }, multiply: function (firstNumber, secondNumber) { return firstNumber * secondNumber; }, divide: function (firstNumber, secondNumber) { return firstNumber / secondNumber; } }; })(this);  
  
    ```  
  
17. In **Projektmappen\-Explorer**, wählen Sie im Kontextmenü für die Datei arithmetic.js **Eigenschaften**. Stellen Sie diese Eigenschaften ändern:  
  
    -   Legen Sie die **Include in VSIX** \-Eigenschaft **True**.  
  
    -   Legen Sie die **In Ausgabeverzeichnis kopieren** \-Eigenschaft **immer kopieren**.  
  
18. In **Projektmappen\-Explorer**, wählen Sie im Kontextmenü für das Projekt SimpleMathVSIX **Erstellen**.  
  
19. Nach Abschluss des Buildvorgangs erfolgreich auf das Kontextmenü für das Projekt, wählen Sie **Ordner im Datei\-Explorer öffnen**. Navigieren Sie zu \\bin\\debug\\, und führen Sie `SimpleMathVSIX.vsix` installieren.  
  
20. Wählen Sie die **Installieren** Schaltfläche und lassen Sie die Installation abgeschlossen.  
  
21. Starten Sie Visual Studio neu.  
  
##  <a name="createSampleApp"></a> Zum Erstellen einer Beispielapp verwendet das SDK  
  
1.  Wählen Sie in der Menüleiste **Datei**, **Neu**, **Projekt** aus.  
  
2.  In der Liste der Kategorien unter **JavaScript**, auf **Windows Store**, und wählen Sie dann die **leere App** Vorlage.  
  
3.  In den **Namen** geben `ArithmeticUI`. Klicken Sie auf die Schaltfläche **OK**.  
  
4.  In **Projektmappen\-Explorer**, öffnen Sie das Kontextmenü für das ArithmeticUI\-Projekt, und wählen Sie dann **Hinzufügen**, **Verweis**.  
  
5.  Klicken Sie unter **Windows**, wählen Sie **Extensions**, und beachten Sie, dass **einfache mathematische** wird angezeigt.  
  
6.  Wählen Sie die **einfache mathematische** das Kontrollkästchen, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  In **Projektmappen\-Explorer**, unter **Verweise**, beachten Sie, dass die **einfache mathematische** Verweis wird angezeigt. Erweitern Sie ihn, und beachten Sie, dass ein \\js\\\-Ordner, der arithmetic.js enthält. Öffnen Sie Sie arithmetic.js, um zu bestätigen, dass der Code installiert wurde.  
  
8.  Verwenden Sie den folgenden Code, um den Inhalt von "default.htm" zu ersetzen.  
  
    ```  
    <!DOCTYPE html> <html> <head> <meta charset="utf-8" /> <title>ArithmeticUI</title> <!-- WinJS references --> <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" /> <script src="//Microsoft.WinJS.1.0/js/base.js"></script> <script src="//Microsoft.WinJS.1.0/js/ui.js"></script> <!-- ArithmeticUI references --> <link href="/css/default.css" rel="stylesheet" /> <script src="/js/default.js"></script> <script src="/SimpleMath/js/arithmetic.js"></script> </head> <body> <form> <div id="calculator" class="ms-grid"> <input name="firstNumber" id="firstNumber" type="number" step="any"> <div id="operators"> <button class="operator" type="button">+</button> <button class="operator" type="button">-</button> <button class="operator" type="button">*</button> <button class="operator" type="button">/</button> </div> <input id="secondNumber" type="number"> <button class="calculate" type="button">=</button> <input id="result" type="number" name="result" disabled="" readonly=""> </div> </form> </body> </html>  
    ```  
  
9. Verwenden Sie den nächsten Code, um den Inhalt der \\js\\default.js zu ersetzen.  
  
    ```  
    (function () { "use strict"; var app = WinJS.Application; var operation = null; function calculateResult() { var firstNumber = parseFloat(document.querySelector("#firstNumber").value), secondNumber = parseFloat(document.querySelector("#secondNumber").value), result = 0; if (isNaN(firstNumber) || isNaN(secondNumber)) { result = 0; } else { switch (operation) { case "+": result = Arithmetic.add(firstNumber, secondNumber); break; case "-": result = Arithmetic.subtract(firstNumber, secondNumber); break; case "*": result = Arithmetic.multiply(firstNumber, secondNumber); break; case "/": result = Arithmetic.divide(firstNumber, secondNumber); break; default: } } document.querySelector("#result").value = result.toString(); } app.onactivated = function (args) { document.querySelector("#calculator").addEventListener("click", function (event) { if (event.target.tagName.toLowerCase() === "button") { switch (event.target.className) { case "operator": operation = event.target.innerText; break; case "calculate": calculateResult(); break; default: break; } } }); }; app.start(); })();  
    ```  
  
10. Ersetzen Sie den Inhalt der \\css\\default.css mit dem folgenden Code:  
  
    ```  
    form { display: -ms-grid; -ms-grid-rows: 1fr auto 1fr; -ms-grid-columns: 1fr auto 1fr; height: 100%; width: 100%; } button, input[type=number] { margin-right: 5px; -ms-grid-row-align: center; } #calculator { -ms-grid-column: 2; -ms-grid-row: 2; display: -ms-grid; -ms-grid-rows: 1fr; -ms-grid-columns: auto min-content auto auto auto; } .ms-grid input { width: 5em; } #firstNumber { -ms-grid-column: 1; -ms-grid-row-align: center; } #operators { -ms-grid-column: 2; -ms-grid-row-align: center; } #operators button.operator { margin-bottom: 5px; height: 40px; } #secondNumber { -ms-grid-column: 3; } button.calculate { -ms-grid-column: 4; -ms-grid-row-align: center; height: 40px; } #result { -ms-grid-column: 5; }  
  
    ```  
  
11. Drücken Sie F5 zum Erstellen und Ausführen der app.  
  
12. In der Benutzeroberfläche der app Geben Sie zwei Zahlen, wählen Sie einen Vorgang aus und wählen Sie dann die **\=** Schaltfläche. Das richtige Ergebnis wird angezeigt.  
  
## Siehe auch  
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)