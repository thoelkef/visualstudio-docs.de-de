---
title: 'Exemplarische Vorgehensweise: Erstellen eines SDK mit JavaScript | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697508"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Exemplarische Vorgehensweise: Erstellen eines SDK mit JavaScript
In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie JavaScript verwenden, um ein einfaches mathematisches SDK als Visual Studio-Erweiterung (VSIX) zu erstellen.  Die exemplarische Vorgehensweise ist in folgende Teile unterteilt:

- [So erstellen Sie das SimpleMathVSIX-Erweiterungs-SDK-Projekt](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [So erstellen Sie eine Beispiel-App, die das SDK verwendet](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Für JavaScript gibt es keinen Klassenbibliotheksprojekttyp. In dieser exemplarischen Vorgehensweise wird die Beispieldatei *arithmetic.js* direkt im VSIX-Projekt erstellt. In der Praxis wird empfohlen, die JavaScript- und CSS-Dateien zunächst als Windows Store-App zu erstellen und zu testen, z. B. mithilfe der Vorlage **Leere App,** bevor Sie sie in einem VSIX-Projekt einfügen.

## <a name="prerequisites"></a>Voraussetzungen
 Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>So erstellen Sie das SimpleMathVSIX-Erweiterungs-SDK-Projekt

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

2. Wählen Sie in der Liste der Vorlagenkategorien unter **Visual C-** die Option **Erweiterbarkeit**aus, und wählen Sie dann die **VSIX-Projektvorlage** aus.

3. Geben Sie im Textfeld **Name** die Schaltfläche `SimpleMathVSIX` **OK** an, und wählen Sie sie aus.

4. Wenn der **Visual Studio-Paket-Assistent** angezeigt wird, wählen Sie die Schaltfläche **Weiter** auf der **Willkommensseite** aus, und wählen Sie dann auf **Seite 1 von 7**die Schaltfläche Fertig **stellen** aus.

     Obwohl der **Manifest-Designer** geöffnet wird, wird diese exemplarische Vorgehensweise einfach, indem Sie die Manifestdatei direkt ändern.

5. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für die Datei **source.extension.vsixmanifest,** und wählen Sie dann **Code anzeigen**aus. Verwenden Sie diesen Code, um den vorhandenen Inhalt in der Datei zu ersetzen.

    ```xml
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

6. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **SimpleMathVSIX-Projekt,** und wählen Sie dann**Neues Element** **hinzufügen** > aus.

7. Wählen Sie in der Kategorie **Daten** `SDKManifest.xml` **xml-Datei**aus , benennen Sie die Datei , und wählen Sie die Schaltfläche **Hinzufügen** aus.

8. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für die Datei **SDKManifest.xml,** und wählen Sie dann **Öffnen** aus, um die Datei im **XML-Editor**anzuzeigen.

9. Fügen Sie der **Datei SDKManifest.xml** den folgenden Code hinzu.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü für die Datei **SDKManifest.xml** **Eigenschaften**aus.

11. Legen Sie im **Fenster Eigenschaften** die Include **in VSIX-Eigenschaft** auf **True**fest.

12. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü für das **SimpleMathVSIX-Projekt** die Option**Neuer Ordner** `Redist` **hinzufügen** > aus, und benennen Sie dann den Ordner .

13. Fügen Sie Unterordner unter Redist hinzu, um diese Ordnerstruktur zu erstellen:

     *"Redist" und "CommonConfiguration" ("GemeinsameKonfiguration"" "Neutral" "SimpleMath"-Js\\*

14. Wählen Sie im Kontextmenü für den Ordner **éjs\\ ** die Option**Neues Element** **hinzufügen** > aus.

15. Wählen Sie unter **Visual C-Elemente**die **Webkategorie** aus, und wählen Sie dann das **JavaScript-Dateielement** aus. Benennen Sie `arithmetic.js`die Datei , und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

16. Fügen Sie den folgenden Code in *arithmetic.js*ein:

    ```csharp
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

17. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü für die Datei **arithmetic.js** **Eigenschaften**aus. Nehmen Sie diese Eigenschaftenänderungen vor:

    - Legen Sie die **Include in VSIX-Eigenschaft** auf **True**fest.

    - Legen Sie die **Eigenschaft Copy to Output Directory** auf Immer **kopieren**fest.

18. Wählen Sie im **Projektmappen-Explorer**im Kontextmenü für das **SimpleMathVSIX-Projekt** **Build**aus.

19. Nachdem der Build erfolgreich abgeschlossen wurde, wählen Sie im Kontextmenü für das Projekt **Ordner öffnen im Datei-Explorer**aus. Navigieren Sie zu **,\\**und `SimpleMathVSIX.vsix` führen Sie aus, um es zu installieren.

20. Wählen Sie die **Schaltfläche Installieren** und lassen Sie die Installation abschließen.

21. Starten Sie Visual Studio neu.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>So erstellen Sie eine Beispiel-App, die das SDK verwendet

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

2. Wählen Sie in der Liste der Vorlagenkategorien unter **JavaScript** **Windows Store**aus, und wählen Sie dann die Vorlage **Leere App** aus.

3. Geben **Name** Sie `ArithmeticUI`im Feld Name an. Klicken Sie auf die Schaltfläche **OK** .

4. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das **ArithmeticUI-Projekt,** und wählen Sie dann**Referenz** **hinzufügen** > aus.

5. Wählen Sie unter **Windows** **Erweiterungen**aus, und beachten Sie, dass **Einfache Mathematik** angezeigt wird.

6. Aktivieren Sie das Kontrollkästchen **Einfache Mathematik,** und wählen Sie dann die Schaltfläche **OK** aus.

7. Beachten Sie im **Projektmappen-Explorer**unter **Referenzen,** dass der Verweis auf **einfache Mathematik** angezeigt wird. Erweitern Sie ihn, und beachten Sie, dass es einen Ordner mit dem Ordner **"arithmetic.js"** gibt. **\\ ** Sie können **arithmetic.js** öffnen, um zu bestätigen, dass Ihr Quellcode installiert wurde.

8. Verwenden Sie den folgenden Code, um den Inhalt von *default.htm*zu ersetzen.

   ```html
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

9. Verwenden Sie den folgenden Code, um den Inhalt von *.js-default.js*zu ersetzen.

    ```csharp
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

10. Ersetzen Sie den Inhalt von *.css-default.css* durch diesen Code:

    ```xml
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

11. Wählen Sie die **F5-Taste** aus, um die App zu erstellen und auszuführen.

12. Geben Sie in der App-Benutzeroberfläche zwei beliebige Zahlen **=** ein, wählen Sie einen Vorgang aus, und wählen Sie dann die Schaltfläche aus. Das richtige Ergebnis wird angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Erstellen eines Software Development Kits](../extensibility/creating-a-software-development-kit.md)
