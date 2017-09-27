---
title: Aufbau eines Tests der programmierten UI | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 23
ms.author: douge
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: d85e24701fd6bc31852fff3927f3698210681b82
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomy of a Coded UI Test
Wenn Sie einen Test der programmierten UI in einem UI-Testprojekt erstellen, werden der Projektmappe mehrere Dateien hinzugefügt. In diesem Thema verwenden wir ein Beispiel für einen Test der programmierten UI, um diese Dateien zu untersuchen.  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
## <a name="contents-of-a-coded-ui-test"></a>Inhalt eines Tests der programmierten UI  
 Wenn Sie einen Test der programmierten UI erstellen, erstellt der **Test-Generator der programmierten UI** eine Zuordnung der getesteten Benutzeroberfläche (UI) sowie die Testmethoden, Parameter und Assertionen für alle Tests. Zudem wird eine Klassendatei für jeden Test erstellt.  
  
|Datei|Inhalt|Bearbeitbar?|  
|----------|--------------|---------------|  
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Deklarationsabschnitt](#UIMapDesignerFile)<br /><br /> [UIMap-Klasse](#UIMapClass) (partiell, automatisch generiert)<br /><br /> [Methoden](#UIMapMethods)<br /><br /> [Eigenschaften](#UIMapProperties)|Nein|  
|[UIMap.cs](#UIMapCS)|[UIMap-Klasse](#UIMapCS) (partiell)|Ja|  
|[CodedUITest1.cs](#CodedUITestCS)|[CodedUITest1-Klasse](#CodedUITestCS)<br /><br /> [Methoden](#CodedUITestMethods)<br /><br /> [Eigenschaften](#CodedUITestProperties)|Ja|  
|[UIMap.uitest](#UIMapuitest)|Die XML-Zuordnung der Benutzeroberfläche für den Test.|Nein|  
  
###  <a name="UIMapDesignerFile"></a> UIMap.Designer.cs  
 Diese Datei enthält Code, der beim Erstellen eines Tests automatisch vom **Test-Generator der programmierten UI** erstellt wird. Diese Datei wird jedes Mal neu erstellt, wenn ein Test geändert wird. In dieser Datei kann daher kein Code hinzugefügt oder geändert werden.  
  
#### <a name="declarations-section"></a>Deklarationsabschnitt  
 Dieser Abschnitt enthält die folgenden Deklarationen für eine Windows-Benutzeroberfläche.  
  
```csharp  
using System;  
using System.CodeDom.Compiler;  
using System.Collections.Generic;  
using System.Drawing;  
using System.Text.RegularExpressions;  
using System.Windows.Input;  
using Microsoft.VisualStudio.TestTools.UITest.Extension;  
using Microsoft.VisualStudio.TestTools.UITesting;  
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;  
using Microsoft.VisualStudio.TestTools.UnitTesting;  
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;  
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;  
using MouseButtons = System.Windows.Forms.MouseButtons;  
```  
  
 Der <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>-Namespace bezieht sich auf eine Windows-Benutzeroberfläche (UI). Für eine Webseiten-Benutzeroberfläche wird der <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>-Namespace verwendet und für eine Windows Presentation Foundation-Benutzeroberfläche der <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>-Namespace.  
  
####  <a name="UIMapClass"></a> UIMap-Klasse  
 Der nächste Abschnitt der Datei ist die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Klasse.  
  
```  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public partial class UIMap  
```  
  
 Der Klassencode beginnt mit einem <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>, das auf die Klasse angewendet wird, die als partielle Klasse deklariert wird. Sie werden feststellen, dass das Attribut außerdem auf jede Klasse in dieser Datei angewendet wird. Eine andere Datei, die weiteren Code für diese Klasse enthalten kann, ist `UIMap.cs`. Diese Datei wird weiter unten erläutert.  
  
 Die generierte `UIMap`-Klasse enthält Code für jede Methode, die beim Aufzeichnen des Tests angegeben wurde.  
  
```  
public void LaunchCalculator()  
public void AddItems()  
public void VerifyTotal()  
public void CleanUp()  
```  
  
 Dieser Teil der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Klasse enthält auch den generierten Code für die einzelnen Eigenschaften, die für die Methoden erforderlich sind.  
  
```  
public virtual LaunchCalculatorParams LaunchCalculatorParams  
public virtual AddItemsParams AddItemsParams  
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues  
public virtual CalculateItemsParams CalculateItemsParams  
public virtual VerifyMathAppTotalExpectedValues   
    VerifyMathAppTotalExpectedValues  
public UIStartMenuWindow UIStartMenuWindow  
public UIRunWindow UIRunWindow  
public UICalculatorWindow UICalculatorWindow  
public UIStartWindow UIStartWindow  
public UIMathApplicationWindow UIMathApplicationWindow  
```  
  
#####  <a name="UIMapMethods"></a> UIMap-Methoden  
 Jede Methode verfügt über eine Struktur, die der `AddItems()`-Methode ähnelt. Dies wird im Anschluss an den Code, der aus Gründen der Übersichtlichkeit mit Zeilenumbrüchen dargestellt ist, ausführlicher erläutert.  
  
```  
/// <summary>  
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.  
/// </summary>  
public void AddItems()  
{  
    #region Variable Declarations  
    WinControl uICalculatorDialog =   
        this.UICalculatorWindow.UICalculatorDialog;  
    WinEdit uIItemEdit =   
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;  
    #endregion  
  
    // Type '{NumPad7}' in 'Calculator' Dialog  
    Keyboard.SendKeys(uICalculatorDialog,   
        this.AddItemsParams.UICalculatorDialogSendKeys,   
        ModifierKeys.None);  
  
    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    Keyboard.SendKeys(uIItemEdit,   
        this.AddItemsParams.UIItemEditSendKeys,   
        ModifierKeys.None);  
}  
```  
  
 Der Zusammenfassungskommentar für die einzelnen Methodendefinitionen gibt Aufschluss darüber, welche Klasse für Parameterwerte dieser Methode verwendet wird. In diesem Fall ist es die `AddItemsParams`-Klasse, die weiter unten in der `UIMap.cs`-Datei definiert wird. Dies ist auch der Werttyp, der von der `AddItemsParams`-Eigenschaft zurückgegeben wird.  
  
 Am Anfang des Methodencodes befindet sich ein `Variable Declarations`-Abschnitt, in dem lokale Variablen für die von der Methode verwendeten UI-Objekte definiert werden.  
  
 In dieser Methode sind sowohl `UIItemWindow` als auch `UIItemEdit` Eigenschaften, auf die mithilfe der `UICalculatorWindow`-Klasse zugegriffen wird. Diese wird weiter unten in der `UIMap.cs`-Datei definiert.  
  
 In den nächsten Zeilen wird mit Eigenschaften des `AddItemsParams`-Objekts Text von der Tastatur an die Rechneranwendung gesendet.  
  
 Die `VerifyTotal()`-Methode weist eine ähnliche Struktur auf und enthält den folgenden Assertionscode.  
  
```  
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '  
Assert.AreEqual(  
    this.VerifyTotalExpectedValues.UIItemEditText,   
    uIItemEdit.Text);  
```  
  
 Der Textfeldname wird als unbekannt aufgeführt, da der Entwickler der Windows-Rechneranwendung keinen öffentlich verfügbaren Namen für das Steuerelement bereitgestellt hat. Bei der <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>-Methode tritt ein Fehler auf, wenn der tatsächliche Wert nicht dem erwarteten Wert entspricht. In diesem Fall kommt es bei dem Test zu einem Fehler. Beachten Sie außerdem, dass der erwartete Wert ein Dezimaltrennzeichen gefolgt von einem Leerzeichen enthält. Wenn Sie die Funktion dieses spezifischen Tests ändern müssen, müssen Sie dieses Dezimaltrennzeichen und das Leerzeichen berücksichtigen.  
  
#####  <a name="UIMapProperties"></a> UIMap-Eigenschaften  
 Der Code für die einzelnen Eigenschaften ist in der gesamten Klasse ebenfalls weitgehend standardisiert. Der folgende Code für die `AddItemsParams`-Eigenschaft wird in der `AddItems()`-Methode verwendet.  
  
```  
public virtual AddItemsParams AddItemsParams  
{  
    get  
    {  
        if ((this.mAddItemsParams == null))  
        {  
            this.mAddItemsParams = new AddItemsParams();  
        }  
        return this.mAddItemsParams;  
    }  
}  
```  
  
 Beachten Sie, dass die Eigenschaft den Wert in einer privaten lokalen Variable mit dem Namen `mAddItemsParams` speichert, bevor sie ihn zurückgibt. Der Eigenschaftsname und der Klassenname für das zurückgegebene Objekt sind identisch. Die Klasse wird weiter unten in der `UIMap.cs`-Datei definiert.  
  
 Alle von einer Eigenschaft zurückgegebenen Klassen sind ähnlich strukturiert. Das folgende Beispiel zeigt die `AddItemsParams`-Klasse.  
  
```  
/// <summary>  
/// Parameters to be passed into 'AddItems'  
/// </summary>  
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]  
public class AddItemsParams  
{  
    #region Fields  
    /// <summary>  
    /// Type '{NumPad7}' in 'Calculator' Dialog  
    /// </summary>  
    public string UICalculatorDialogSendKeys = "{NumPad7}";  
  
    /// <summary>  
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box  
    /// </summary>  
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";  
    #endregion  
}  
```  
  
 Wie alle Klassen in der `UIMap.cs`-Datei beginnt diese Klasse mit dem <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. Diese kleine Klasse enthält den `Fields`-Abschnitt, in dem die Zeichenfolgen definiert sind, die als Parameter für die <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>-Methode in der zuvor erläuterten `UIMap.AddItems()`-Methode verwendet werden. Sie können vor dem Aufruf der Methode, in der diese Parameter verwendet werden, Code schreiben, um die Werte in diesen Zeichenfolgenfeldern zu ersetzen.  
  
###  <a name="UIMapCS"></a> UIMap.cs  
 Standardmäßig enthält diese Datei eine partielle `UIMap`-Klasse ohne Methoden oder Eigenschaften.  
  
#### <a name="uimap-class"></a>UIMap-Klasse  
 In dieser Klasse können Sie benutzerdefinierten Code erstellen, um die Funktion der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Klasse zu erweitern. Der in dieser Datei erstellte Code wird nicht bei jeder Änderung eines Tests vom **Test-Generator der programmierten UI** erneut generiert.  
  
 In allen Teilen der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> können die Methoden und Eigenschaften aus einem beliebigen anderen Teil der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>-Klasse verwendet werden.  
  
###  <a name="CodedUITestCS"></a> CodedUITest1.cs  
 Diese Datei wird vom **Test-Generator der programmierten UI** generiert, aber nicht bei jeder Änderung des Tests neu erstellt. Der Code in dieser Datei kann daher geändert werden. Der Name der Datei wird auf Grundlage des Namens generiert, den Sie beim Erstellen für den Test angegeben haben.  
  
#### <a name="codeduitest1-class"></a>CodedUITest1-Klasse  
 Standardmäßig enthält diese Datei nur die Definition für eine Klasse.  
  
```  
[CodedUITest]  
public class CodedUITest1  
```  
  
 Das "T:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute" wird automatisch auf die Klasse angewendet, sodass sie vom Testframework als Testerweiterung erkannt werden kann. Dies ist keine partielle Klasse. Der gesamte Klassencode ist in dieser Datei enthalten.  
  
#####  <a name="CodedUITestProperties"></a> CodedUITest1-Eigenschaften  
 Die Klasse enthält zwei Standardeigenschaften, die sich am Ende der Datei befinden. Sie dürfen nicht geändert werden.  
  
```  
/// <summary>  
/// Gets or sets the test context which provides  
/// information about and functionality for the current test run.  
///</summary>  
public TestContext TestContext  
public UIMap UIMap  
```  
  
#####  <a name="CodedUITestMethods"></a> CodedUITest1-Methoden  
 Standardmäßig enthält die Klasse nur eine Methode.  
  
```  
public void CodedUITestMethod1()  
```  
  
 Diese Methode ruft jede `UIMap`-Methode auf, die Sie beim Aufzeichnen des Tests angegeben haben. Informationen dazu finden Sie im Abschnitt zur [UIMap-Klasse](#UIMapClass).  
  
 Ein Bereich mit dem Titel `Additional test attributes` enthält zwei optionale Methoden, sofern die Auskommentierung aufgehoben wurde.  
  
```  
// Use TestInitialize to run code before running each test   
[TestInitialize()]  
public void MyTestInitialize()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.LaunchCalculator();  
}  
  
// Use TestCleanup to run code after each test has run  
[TestCleanup()]  
public void MyTestCleanup()  
{  
    // To generate code for this test, select "Generate Code for Coded   
    // UI Test" from the shortcut menu and select one of the menu items.  
    // For more information on generated code, see   
    // http://go.microsoft.com/fwlink/?LinkId=179463  
  
    // You could move this line from the CodedUITestMethod1() method  
    this.UIMap.CloseCalculator();  
}  
```  
  
 Der `MyTestInitialize()`-Methode ist das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> zugewiesen, wodurch das Testframework angewiesen wird, diese Methode vor allen anderen Testmethoden aufzurufen. Desgleichen ist der `MyTestCleanup()`-Methode das <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> zugewiesen, wodurch das Testframework angewiesen wird, diese Methode nach allen anderen Testmethoden aufzurufen. Die Verwendung dieser Methoden ist optional. Für diesen Test könnte die `UIMap.LaunchCalculator()`-Methode von `MyTestInitialize()` und die `UIMap.CloseCalculator()`-Methode von `MyTestCleanup()` aufgerufen werden, anstatt von `CodedUITest1Method1()`.  
  
 Wenn Sie dieser Klasse weitere Methoden mit dem <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute> hinzufügen, wird im Rahmen des Tests jede Methode vom Testframework aufgerufen.  
  
###  <a name="UIMapuitest"></a> UIMap.uitest  
 Dies ist eine XML-Datei, die die Struktur der Aufzeichnung des Tests der programmierten UI und all seiner Teile darstellt. Dies beinhaltet die Aktionen und Klassen sowie die Methoden und Eigenschaften dieser Klassen. Die Datei [UIMap.Designer.cs](#UIMapDesignerFile) enthält den Code, der vom Generator für programmierte UI generiert wird, um die Struktur des Tests zu reproduzieren, und stellt die Verbindung mit dem Testframework bereit.  
  
 Die `UIMap.uitest`-Datei kann nicht direkt bearbeitet werden. Sie können den Test jedoch mit dem Generator für programmierte UI ändern, wodurch die Dateien `UIMap.uitest` und [UIMap.Designer.cs](#UIMapDesignerFile) automatisch geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>   
 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.CodedUITestAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>   
 [Verwenden von Benutzeroberflächenautomatisierung zum Testen des Codes](../test/use-ui-automation-to-test-your-code.md)   
 [Erstellen von Tests der codierten UI](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Best Practices for Coded UI Tests (Bewährte Methoden für Tests der programmierten UI)](../test/best-practices-for-coded-ui-tests.md)   
 [Testing a Large Application with Multiple UI Maps (Testen einer großen Anwendung mit mehreren UI-Zuordnungen)](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Unterstützte Konfigurationen und Plattformen für Tests der programmierten UI und Aktionsaufzeichnungen](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

