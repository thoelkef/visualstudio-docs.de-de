---
title: Schnelle Aktionen | Microsoft-Dokumentation
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: kempb
ms.author: kempb
manager: ghogen
dev_langs:
- CSharp
- VB
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: ec2ae70312c7cb5f26630246046cadc7c210e1c2
ms.contentlocale: de-de
ms.lasthandoff: 05/26/2017

---
# <a name="quick-actions"></a>Schnelle Aktionen

Mit [schnellen Aktionen](refactoring-code-generation-quick-actions.md#quick-actions) können Sie ganz leicht Code mit einer einzelnen Aktion umgestalten, generieren oder anderweitig ändern.  Während es viele schnelle Aktionen gibt, die entweder nur für C# oder Visual Basic gelten, gibt es auch einige, die sowohl für C#- als auch Visual Basic-Projekte gültig sind.  Diese können mithilfe des Glühbirnensymbols ![Kleines Glühbirnensymbol](~/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") oder durch Drücken von **STRG + .** angewendet werden,  wenn der Cursor sich in der entsprechenden Codezeile befindet.

Sie sehen eine Glühbirne, wenn eine rote Wellenlinie vorhanden ist und Visual Studio über eine Empfehlung verfügt, um das Problem zu beheben. Wenn beispielsweise ein Fehler durch eine rote Wellenlinie gekennzeichnet ist, wird eine Glühbirne angezeigt, wenn Behebungsmaßnahmen für diesen Fehler verfügbar sind. Für jede Sprache können Drittanbieter benutzerdefinierte Diagnosen und Empfehlungen bereitstellen, beispielsweise als Bestandteil eines SDKs. Anhand dieser Regeln leuchten Visual Studio-Glühbirnen dann auf.  

### <a name="to-see-a-light-bulb"></a>So zeigen Sie eine Glühbirne an  

1. In vielen Fällen werden Glühbirnen spontan angezeigt, wenn Sie mit dem Mauszeiger auf die Position eines Fehlers zeigen, oder am linken Rand des Editors, wenn Sie die Einfügemarke in eine Zeile verschieben, die einen Fehler enthält. Wenn eine rote Wellenlinie angezeigt wird, können Sie den Mauszeiger darüber bewegen, um die Glühbirne anzuzeigen. Sie können auch veranlassen, dass eine Glühbirne angezeigt wird, wenn Sie die Maus oder Tastatur verwenden, um zu einem beliebigen Punkt in der Zeile zu wechseln, wo das Problem auftritt.  

2. Drücken Sie **STRG + .** an einer beliebigen Stelle in einer Zeile, um die Glühbirne aufzurufen und direkt zur Liste mit den potenziellen Fehlerbehebungen zu wechseln.  

   ![Glühbirne mit Mauszeigerbewegung](../ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### <a name="to-see-potential-fixes"></a>So zeigen Sie potenzielle Fehlerbehebungen an  
Klicken Sie entweder auf den Pfeil nach unten oder auf den Link zum Anzeigen von potenziellen Fehlerbehebungen, um eine Liste von schnellen Aktionen anzuzeigen, die die Glühbirne für Sie vornehmen kann.  

![Erweiterte Glühbirne](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## <a name="common-quick-actions"></a>Häufige schnelle Aktionen
Dies sind einige der am häufigsten vorkommenden schnellen Aktionen, die sowohl für C#- als auch für Visual Basic-Code gültig sind.

### <a name="add-missing-casesdefault-caseboth"></a>Fügen Sie fehlende Fälle/einen Standardfall/beides hinzu
Wenn Sie eine `switch`-Anweisung in C# oder eine `Select Case`-Anweisung in Visual Basic erstellen, können Sie mit einer Codeaktion automatisch fehlende Fallelemente, eine Standardfallanweisung oder beides hinzufügen.  Für eine leere Anweisung, wie die folgende:

```CSharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```VB
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

Durch die schnelle Aktion **Add Both** (Beides hinzufügen) für das Ausfüllen sowohl fehlender Fälle und als auch eines Standardfalls wird Folgendes erstellt:

```CSharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```VB
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

### <a name="correct-misspelled-type"></a>Korrigieren eines falsch geschriebener Typs
Wenn Sie aus Versehen einen Typ in Visual Studio falsch schreiben, korrigiert diese schnelle Aktion den Fehler für Sie automatisch.  Sie sehen diese Elemente im Glühbirnenmenü als **„Ändern des‚*Falsch geschriebenen Typ*‘ in ‚*korrekten Typ*‘**.  Zum Beispiel:

```CSharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```VB
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

### <a name="remove-unnecessary-cast"></a>Nicht benötigte Umwandlung entfernen
Wenn Sie einen Typ in einen anderen Typ umwandeln, der keine Umwandlung benötigt, entfernt das Element der schnellen Aktion **Remove Unnecessary Cast** (Nicht benötigte Umwandlung entfernen) die Umwandlung aus Ihrem Code.

```CSharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```VB
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### <a name="replace-method-with-property--replace-property-with-method"></a>Eine Methode durch eine Eigenschaft ersetzen/eine Eigenschaft durch eine Methode ersetzen
Diese schnellen Aktionen konvertieren eine Methode in eine Eigenschaft und andersherum.  Das unten stehende Beispiel veranschaulicht die Änderung von einer Methode in eine Eigenschaft.  Tauschen Sie im anderen Fall einfach die Bereiche *Vorher* und *Nachher* miteinander.

```CSharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

```VB
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### <a name="make-method-synchronous"></a>Methode als synchron deklarieren
Wenn Sie das Schlüsselwort `async`/`Async` für eine Methode verwenden, wird erwartet, dass das Schlüsselwort `await`/`Await` auch irgendwo innerhalb der Methode verwendet wird.  Sollte dies nicht der Fall sein, erscheint eine schnelle Aktion, die es Ihnen ermöglicht, die Methode als synchron zu deklarieren, indem Sie das Schlüsselwort `async`/`Async` entfernen und den Rückgabetyp anpassen.  Verwenden Sie die Option **Make Method Synchronous** (Methode als synchron deklarieren) aus dem Menü für schnelle Aktionen.

```CSharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```VB
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

### <a name="make-method-asynchronous"></a>Methode als asynchron deklarieren
Wenn Sie das Schlüsselwort `await`/`Await` innerhalb einer Methode verwenden, wird erwartet, dass die Methode selbst mit dem Schlüsselwort `async`/`Async` gekennzeichnet ist.  Sollte dies allerdings nicht der Fall sein, erscheint eine schnelle Aktion, die es Ihnen ermöglicht, die Methode als asynchron zu deklarieren.  Verwenden Sie die Option **Make method/Function asynchronous** (Methode/Funktion als asynchron deklarieren) aus dem Menü für schnelle Aktionen.

```CSharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```VB
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### <a name="remove-unnecesary-usingsimports"></a>Nicht benötigtes Usings/Imports entfernen
Die schnelle Aktion **Remove Unnecessary Usings/Imports** (Nicht benötigtes Usings/Imports entfernen) entfernt jede nicht benötigte `using`- und `Import`-Anweisung aus der aktuellen Datei.  Wenn Sie dieses Element auswählen, werden nicht benötigte import-Anweisungen des Namespaces umgehend entfernt.

### <a name="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution"></a>Usings/Imports für Typen in Verweisassemblys, NuGet-Paketen oder anderen Typen in Ihrer Projektmappe hinzufügen
Using-Typen in anderen Projekten in Ihrer Projektmappe zeigen die schnelle Aktion automatisch an; allerdings müssen alle anderen auf der Registerkarte **Tools > Options > C#** (Tools > Optionen > C#) oder **Basic > Advanced** (Basic > Erweitert) aktiviert werden:  

* Usings/Imports für Typen in Verweisassemblys vorschlagen
* Usings/Imports für Typen in NuGet-Paketen vorschlagen

Wenn dies aktiviert ist, wird die using/import-Anweisung erstellt, wenn Sie einen Typ in einem Namespace verwenden, der zu diesem Zeitpunkt nicht importiert ist, aber in einer Verweisassembly oder einem NuGet-Paket vorhanden ist.

```CSharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```VB
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### <a name="convert-to-interpolated-string"></a>Konvertieren in eine interpolierte Zeichenfolge
[Interpolierte Zeichenfolgen](/dotnet/csharp/language-reference/keywords/interpolated-strings) sind eine einfache Möglichkeit, Zeichenfolgen mit eingebetteten Variablen auszudrücken, ähnlich wie mit der **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)**-Methode.  Diese schnelle Aktion erkennt Fälle, in denen Zeichenfolgen verkettet sind oder **String.Format** verwenden, und ändert die Verwendung in eine interpolierte Zeichenfolge.

```CSharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```VB
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

### <a name="remove-merge-conflict-markers"></a>Entfernen von Markierungen für Zusammenführungskonflikte
Diese schnellen Aktionen ermöglichen das Auflösen von Zusammenführungskonflikten durch das „Vornehmen einer Änderung“, wodurch der in Konflikt stehende Code und die Markierungen entfernt werden. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Auflösen von Zusammenführungskonflikten](~/ide/media/vside-refactoring-merge-conflicts.png)

### <a name="add-null-checks-for-parameters"></a>Hinzufügen von Überprüfungen auf NULL für Parameter
Diese schnelle Aktion ermöglicht Ihnen das Hinzufügen einer Prüfung zu Ihrem Code, um zu ermitteln, ob ein Parameter NULL ist. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Hinzufügen von Prüfung auf NULL](~/ide/media/vside-refactoring-nullcheck.png)

### <a name="constructor-generator-improvements"></a>Verbesserungen beim Generator von Konstruktoren
Wenn Sie einen Konstruktor erstellen, ermöglicht Ihnen diese schnelle Aktion das Auswählen der zu erstellenden Eigenschaften oder Felder oder das Generieren des Konstruktors aus einem leeren Textkörper. Sie können sie auch verwenden, um von der Aufrufsite aus einem vorhandenen Konstruktor Parameter hinzuzufügen. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Generieren von Konstruktoren](~/ide/media/vside-refactoring-constructors.png)

### <a name="remove-unused-variables"></a>Entfernen nicht verwendeter Variablen
Diese schnelle Aktion ermöglicht Ihnen das Entfernen von Variablen, die zwar deklariert, aber nie in Ihrem Code verwendet wurden. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Nicht verwendete Variablen](~/ide/media/vside-refactoring-unusedvars.png)

### <a name="generate-overrides"></a>Generieren von Überschreibungen
Mit dieser schnellen Aktion können Sie eine Überschreibung anhand einer leeren Zeile in einer Klasse oder Struktur erstellen. Im Dialogfeld **Member auswählen** können Sie die zu überschreibenden Member auswählen. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Überschreibungen](~/ide/media/vside-refactoring-overrides.png)

![Refactoring: Dialogfeld „Überschreibungen“](~/ide/media/vside-refactoring-overrides-dialog.png)

### <a name="change-base-for-numeric-literals"></a>Ändern der Basis für numerische Literale
Mithilfe dieser schnellen Aktion können Sie ein numerisches Literal von einem numerischen Basissystem in ein anderes konvertieren. Beispielsweise können Sie eine Zahl in das hexadezimale oder binäre Format ändern. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Ändern der Basis](~/ide/media/vside-refactoring-changebase1.png)

![Refactoring: Ändern der Basis](~/ide/media/vside-refactoring-changebase2.png)

### <a name="insert-digit-separators-into-literals"></a>Einfügen von Zifferntrennzeichen in Literale
Mithilfe dieser schnellen Aktion können Sie Zifferntrennzeichen in Literale einfügen. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

![Refactoring: Ändern von Zifferntrennzeichen](~/ide/media/vside-refactoring-separators.png)

### <a name="convert-if-construct-to-switch"></a>Konvertieren von **if**-Konstrukt in **switch**
Mit dieser schnellen Aktionen können Sie ein **if-then-else**-Konstrukt in ein **switch**-Konstrukt konvertieren. (Nur in Visual Studio 2017 [Version 15.3 - Preview] verfügbar.)

```CSharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);  
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```VB
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

# <a name="see-also"></a>Siehe auch
* [Codeformate und schnelle Aktionen](code-styles-and-quick-actions.md)

