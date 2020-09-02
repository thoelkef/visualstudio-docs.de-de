---
title: Refactoring (c#) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667505"
---
# <a name="refactoring-c"></a>Refactoring (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refactoring ist der Prozess der Verbesserung Ihres Codes, nachdem er geschrieben wurde, indem die interne Struktur des Codes geändert wird, ohne das externe Verhalten des Codes zu ändern.

 Visual c# bietet die folgenden refactoringbefehle im Menü **Refactoring** :

- [Refactoring „Methode extrahieren“ (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Refactoring durch Umbenennen (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Refactoring „Feld kapseln“ (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Refactoring „Schnittstelle extrahieren“ (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Umgestaltung „Parameter entfernen“ (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Refactoring „Parameter neu anordnen“ (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refactoring für mehrere Projekte
 Visual Studio unterstützt das Refactoring von mehreren Projekten für Projekte, die sich in derselben Projekt Mappe befinden. Alle Refactoringvorgänge, bei denen Verweise über Dateien hinweg ordnungsgemäß korrigiert werden, korrigieren diese Verweise für alle Projekte derselben Sprache. Dies funktioniert für alle Projekt-zu-Projekt-Verweise. Wenn Sie z. b. eine Konsolenanwendung haben, die auf eine Klassenbibliothek verweist, werden beim Umbenennen eines Klassen Bibliotheks Typs (mit dem `Rename` Refactoring-Vorgang) auch die Verweise auf den Klassen Bibliothekstyp in der Konsolenanwendung aktualisiert.

## <a name="changes-preview"></a>Vorschau der Änderungen
 Viele Refactoringvorgänge bieten Ihnen die Möglichkeit, alle Verweis Änderungen zu überprüfen, die von einem Umgestaltungs Vorgang für den Code ausgeführt werden, bevor Sie diese Änderungen ausführen. Für diese Umgestaltungs Vorgänge wird im Dialogfeld Umgestaltung die Option **Vorschau der Verweis Änderungen** angezeigt. Nachdem Sie diese Option ausgewählt und den Refactoring-Vorgang akzeptiert haben, wird das **Dialog Feld Vorschau der Änderungen** angezeigt. Beachten Sie, dass das Dialogfeld **Vorschau der Änderungen** über zwei Ansichten verfügt. In der unteren Ansicht wird der Code mit allen Referenz Updates angezeigt, die durch den Refactoring-Vorgang verursacht werden. Wenn Sie im Dialogfeld **Vorschau der Änderungen** auf **Abbrechen** drücken, wird der Umgestaltungs Vorgang beendet, und es werden keine Änderungen an Ihrem Code vorgenommen.

## <a name="refactoring-warnings"></a>Refactoring von Warnungen
 Wenn der Compiler nicht über ein vollständiges Verständnis des Programms verfügt und es möglich ist, dass die Refactoring-Engine nicht alle entsprechenden Verweise aktualisiert, wird das Dialogfeld Warnung angezeigt. Dieses Dialogfeld "Warnung" bietet Ihnen auch die Möglichkeit, den Code im Dialogfeld " **Vorschau der Änderungen** " in der Vorschau anzuzeigen, bevor Sie die Änderungen ausführen.

> [!NOTE]
> Wenn eine Methode einen Syntax Fehler enthält (was in der IDE durch eine rote wellenförmige Unterstreichung angegeben wird), aktualisiert die Refactoring-Engine keine Verweise auf ein Element innerhalb dieser Methode. Dieses Verhalten wird im folgenden Beispiel veranschaulicht.

 Wenn Sie einen Umgestaltungs Vorgang ohne Vorschau der Verweis Änderungen ausführen und im Programm ein Kompilierungsfehler erkannt wird, wird in der Entwicklungsumgebung standardmäßig das Dialogfeld Warnung angezeigt.

 Wenn Sie einen Umgestaltungs Vorgang ausführen, bei dem **Vorschau Referenz Änderungen** aktiviert sind und im Programm ein Kompilierungsfehler erkannt wird, wird in der Entwicklungsumgebung unten im Dialogfeld **Vorschau der Änderungen** die folgende Warnmeldung angezeigt, anstatt das Dialogfeld **Refactoring-Warnung** anzuzeigen:

 **Das Projekt oder eine seiner Abhängigkeiten wird derzeit nicht erstellt. Verweise werden möglicherweise nicht aktualisiert.**

 Diese Refactoring-Warnung ist nur für Refactoringvorgänge verfügbar, die die Option " **Vorschau der Verweis Änderungen** " bereitstellen.

## <a name="error-tolerant-refactoring-and-verification-results"></a>Fehlertolerante Umgestaltung und Überprüfungs Ergebnisse
 Refactoring ist fehlertolerant. Anders ausgedrückt: Sie können ein Refactoring in einem Projekt durchführen, das nicht erstellt werden kann. In diesen Fällen aktualisiert der refactoringprozess jedoch möglicherweise mehrdeutige Verweise nicht ordnungsgemäß.

 Mithilfe des Dialog Felds **Überprüfungs Ergebnisse** können Sie benachrichtigt werden, wenn die Refactoring-Engine Kompilierungsfehler erkennt oder feststellt, dass ein Refactoring-Vorgang versehentlich bewirkt, dass ein Code Verweis an etwas anderes gebunden ist als das, an das es ursprünglich gebunden wurde (Problem der erneuten Bindung).

 Klicken Sie im Menü Extras auf **Optionen**, **um das Überprüfungs** Ergebnis Feature zu aktivieren. Erweitern Sie im Dialogfeld **Optionen** den **Text-Editor**, und erweitern Sie dann **c#**. Klicken Sie auf **erweitert** , und aktivieren Sie das Kontrollkästchen **Ergebnisse der Umgestaltung überprüfen** .

 Im Dialogfeld **Überprüfungs Ergebnisse** wird der Unterschied zwischen zwei Arten von neueinbindungs-Problemen unterschieden.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Verweise, deren Definition nicht mehr das umbenannte Symbol ist
 Diese Art von neueinbindungs-Problem tritt auf, wenn ein Verweis nicht mehr auf ein umbenanntes Symbol verweist. Beachten Sie z. B. folgenden Code:

```csharp
class Example
{
    private int a;
    public Example(int b)
    {
        a = b;
    }
}
```

 Wenn Sie Refactoring zum Umbenennen `a` in verwenden `b` , wird dieses Dialogfeld angezeigt. Der Verweis auf die umbenannte Variable `a` bindet nun an den-Parameter, der an den-Konstruktor übergeben wird, anstatt an das-Feld zu binden.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Verweise, deren Definition jetzt das umbenannte Symbol wird
 Diese Art von neueinbindungs-Problem tritt auf, wenn ein Verweis, der zuvor nicht auf das umbenannte Symbol verwiesen hat, jetzt auf das umbenannte Symbol verweist. Beachten Sie z. B. folgenden Code:

```csharp
class Example
{
    private static void Method(object a) { }
    private static void OtherMethod(int a) { }
    static void Main(string[] args)
    {
        Method(5);
    }
}
```

 Wenn Sie Refactoring zum Umbenennen `OtherMethod` in verwenden `Method` , wird dieses Dialogfeld angezeigt. Der Verweis in `Main` verweist jetzt auf die überladene Methode, die `int` anstelle der überladenen Methode, die einen-Parameter akzeptiert, einen-Parameter akzeptiert `object` .

## <a name="see-also"></a>Weitere Informationen
 [Verwenden der Visual Studio-Entwicklungsumgebung für c#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) Gewusst [wie: Wiederherstellen von c#-refactoringausschnitten](../ide/how-to-restore-csharp-refactoring-snippets.md)