---
title: 'Exemplarische Vorgehensweise: Erstellen einer SDKS mit JavaScript | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2132269329c8b6af3ac846596adea7b3462db5bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Exemplarische Vorgehensweise: Erstellen einer SDKS mit JavaScript
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie JavaScript verwenden, um eine einfache mathematische SDK als eine Visual Studio-Erweiterung (VSIX) zu erstellen.  Die exemplarische Vorgehensweise ist in folgende Teile gegliedert:  
  
-   [Zum Erstellen des SimpleMathVSIX Erweiterung-SDK-Projekts](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Eine Beispiel-app erstellen, die das SDK verwendet](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Für JavaScript müssen Sie kein Klasse Library-Projekt-Typ vorhanden ist. In dieser exemplarischen Vorgehensweise wird die Beispieldatei arithmetic.js direkt im VSIX-Projekt erstellt. In der Praxis wird empfohlen, dass Sie zuerst erstellen und Testen Sie die JavaScript und CSS-Dateien als Windows Store-Apps – z. B. mithilfe der **leere App** Vorlage – bevor Sie sie in einem VSIX-Projekt einfügen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Zum Erstellen des SimpleMathVSIX Erweiterung-SDK-Projekts  
  
1.  Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.  
  
2.  In der Liste der Vorlagenkategorien unter **Visual C#-**Option **Erweiterbarkeit**, und wählen Sie dann die **VSIX-Projekt** Vorlage.  
  
3.  In der **Namen** Text geben `SimpleMathVSIX` , und wählen Sie die **OK** Schaltfläche.  
  
4.  Wenn die **Visual Studio-Paketassistent** angezeigt wird, wählen Sie die **Weiter** auf die Schaltfläche der **Willkommen** Seite, und klicken Sie dann auf **Seite 1 von 7**, wählen Sie die **Fertig stellen** Schaltfläche.  
  
     Obwohl die **Manifest-Designer** geöffnet wird, wir werden in dieser exemplarischen Vorgehensweise auch einfach halten, durch direktes Ändern der Manifestdatei.  
  
5.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die Datei "Source.Extension.vsixmanifest", und wählen Sie dann **Code anzeigen**. Verwenden Sie diesen Code, um den vorhandenen Inhalt der Datei zu ersetzen.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das SimpleMathVSIX-Projekt, und wählen Sie dann **hinzufügen**, **neues Element**.  
  
7.  In der **Daten** Kategorie wählen **XML-Datei**, nennen Sie die Datei `SDKManifest.xml`, und wählen Sie die **hinzufügen** Schaltfläche.  
  
8.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für die SDKManifest.xml-Datei, und wählen Sie dann **öffnen** zum Anzeigen der Datei in die **XML-Editor**.  
  
9. Fügen Sie den folgenden Code in die Datei SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. In **Projektmappen-Explorer**, wählen Sie im Kontextmenü für die Datei SDKManifest.xml **Eigenschaften**.  
  
11. In der **Eigenschaften** legen die **Include in VSIX** Eigenschaft **"true"**.  
  
12. In **Projektmappen-Explorer**, wählen Sie im Kontextmenü für das Projekt SimpleMathVSIX **hinzufügen**, **neuer Ordner**, und benennen Sie den Ordner `Redist`.  
  
13. Fügen Sie die Unterordner Redist dieser Ordnerstruktur zu erstellen:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. Wählen Sie im Kontextmenü für den Ordner \js\ **hinzufügen**, **neues Element**.  
  
15. Klicken Sie unter **Visual C#-Elemente**, wählen die **Web** Kategorie, und wählen Sie dann die **JavaScript-Datei** Element. Nennen Sie die Datei `arithmetic.js`, und wählen Sie dann die **hinzufügen** Schaltfläche.  
  
16. Fügen Sie arithmetic.js mit den folgenden Code:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. In **Projektmappen-Explorer**, wählen Sie im Kontextmenü für die Datei arithmetic.js **Eigenschaften**. Diese eigenschaftenänderungen vornehmen:  
  
    -   Legen Sie die **Include in VSIX** Eigenschaft **"true"**.  
  
    -   Legen Sie die **in Ausgabeverzeichnis kopieren** Eigenschaft **immer kopieren**.  
  
18. In **Projektmappen-Explorer**, wählen Sie im Kontextmenü für das Projekt SimpleMathVSIX **erstellen**.  
  
19. Wählen Sie nach Abschluss des Buildvorgangs erfolgreich auf das Kontextmenü für das Projekt **Ordner in Datei-Explorer öffnen**. Navigieren Sie zu \bin\debug\\, und führen Sie `SimpleMathVSIX.vsix` , es zu installieren.  
  
20. Wählen Sie die **installieren** Schaltfläche und legen Sie die Installation abgeschlossen.  
  
21. Starten Sie Visual Studio neu.  
  
##  <a name="createSampleApp"></a> Eine Beispiel-app erstellen, die das SDK verwendet  
  
1.  Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.  
  
2.  In der Liste der Vorlagenkategorien unter **JavaScript**Option **Windows Store**, und wählen Sie dann die **leere App** Vorlage.  
  
3.  In der **Namen** geben `ArithmeticUI`. Klicken Sie auf die Schaltfläche **OK** .  
  
4.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für das ArithmeticUI-Projekt, und wählen Sie dann **hinzufügen**, **Verweis**.  
  
5.  Klicken Sie unter **Windows**, wählen Sie **Erweiterungen**, und beachten Sie, dass **einfache mathematische** wird angezeigt.  
  
6.  Wählen Sie die **einfache mathematische** Kontrollkästchen, und wählen Sie dann die **OK** Schaltfläche.  
  
7.  In **Projektmappen-Explorer**unter **Verweise**, beachten Sie, dass die **einfache mathematische** Verweis wird angezeigt. Erweitern Sie ihn, und beachten Sie, dass es ein \js\-Ordner, der Arithmetic.js enthält. Sie können öffnen arithmetic.js, um zu bestätigen, dass Quellcode installiert wurde.  
  
8.  Verwenden Sie den folgenden Code, um den Inhalt von "default.htm" zu ersetzen.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Verwenden Sie den nächsten Code, um den Inhalt der \js\default.js ersetzen.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Ersetzen Sie den Inhalt der \css\default.css mit dem folgenden Code ein:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Wählen Sie die Taste F5, um die app erstellen und ausführen.  
  
12. Geben Sie in der Benutzeroberfläche der app, alle zwei Zahlen, wählen Sie einen Vorgang, und wählen Sie dann die **=** Schaltfläche. Das richtige Ergebnis wird angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)