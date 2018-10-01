---
title: Refactoring (c#) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e74b540808c07aba5211ab69ea8270f6000b2a19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522277"
---
# <a name="refactoring-c"></a>Refactoring (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refactoring, ist der Prozess, der den Code zu verbessern, nachdem dieser geschrieben wurde, indem Sie die interne Struktur des Codes ändern, ohne das externe Verhalten des Codes zu ändern.  
  
 Visual c# bietet die folgenden Befehle für die Umgestaltung für die **Refactoring** Menü:  
  
-   [Refactoring „Methode extrahieren“ (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refactoring durch Umbenennen (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Refactoring „Feld kapseln“ (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Refactoring „Schnittstelle extrahieren“ (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Umgestaltung „Parameter entfernen“ (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Refactoring „Parameter neu anordnen“ (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Refactoring mit mehreren Projekten  
 Visual Studio unterstützt mit mehreren Projekten refactoring für Projekte, die sich in derselben Projektmappe befinden. Alle der Umgestaltungsvorgänge, die Verweise auf Dateien zu korrigieren, korrigieren diese Verweise für alle Projekte die gleiche Sprache. Dies funktioniert für alle Verweise von Projekt-zu-Projekt. Für, wenn Sie z. B. eine Konsolenanwendung, die eine Klassenbibliothek verweist, wenn Sie einen Typ "Klassenbibliothek" Umbenennen (mithilfe der `Rename` refactoringvorgang), die Verweise auf den Typ "Klassenbibliothek" in der Konsolenanwendung werden ebenfalls aktualisiert.  
  
## <a name="changes-preview"></a>Vorschau der Änderungen  
 Viele Umgestaltungsvorgänge bieten die Möglichkeit für alle verweisänderungen, die auch eine einn refactoring mit Umbenennung für Ihren Code vor dem Ausführen eines Commits für an diese Änderungen zu überprüfen. Für diese Vorgänge die Umgestaltung einer **Vorschau der verweisänderungen** Option wird das Dialogfeld "Umgestaltung" angezeigt. Nach dem Auswählen dieser Option und den Umgestaltungsvorgang, akzeptiert die **Preview Changes Dialog Box** wird angezeigt. Beachten Sie, dass die **Vorschau der Änderungen** Dialogfeld verfügt über zwei Ansichten. Die Ansicht im unteren zeigt Ihren Code mit den Verweis Updates aufgrund des Umgestaltungsvorgangs. Drücken Sie **Abbrechen** auf die **Vorschau der Änderungen** Dialogfeld wird den Umgestaltungsvorgang beendet, und werden keine Änderungen an Ihrem Code vorgenommen.  
  
## <a name="refactoring-warnings"></a>Umgestaltung von Warnungen  
 Wenn der Compiler verfügt nicht über ein vollständiges Verständnis einer des Programms, und es ist möglich, dass die umgestaltungs-Engine alle entsprechenden Verweise nicht aktualisiert werden kann, wird das Dialogfeld "Warnung" angezeigt. Das Dialogfeld "Warnung" bietet außerdem die Gelegenheit für Sie Ihren Code in Vorschau anzeigen, die **Vorschau der Änderungen** (Dialogfeld), bevor Sie Änderungen zu übernehmen.  
  
> [!NOTE]
>  Wenn eine Methode einen Syntaxfehler enthält (die die IDE mit einer roten wellenförmigen Unterstreichung angibt), aktualisiert die umgestaltungs-Engine keine Verweise auf ein Element innerhalb der betreffenden Methode. Das folgende Beispiel veranschaulicht dieses Verhalten.  
  
 In der Standardeinstellung bei Ausführung ein Umgestaltungsvorgangs ohne Vorschau Verweis ändert ein Kompilierungsfehler in Ihrem Programm erkannt, und die Entwicklungsumgebung zeigt das Dialogfeld "Warnung".  
  
 Wenn Sie einen Umgestaltung Vorgang ausgeführt werden, die **Vorschau der verweisänderungen** aktiviert ein Kompilierungsfehler in Ihrem Programm erkannt, und die Entwicklungsumgebung wird die folgende Warnmeldung angezeigt, am unteren Rand der **Vorschau der Änderungen** Dialogfeld durch Anzeigen der **Refactoring Warnung** Dialogfeld:  
  
 **Das Projekt oder eine ihrer Abhängigkeiten wird derzeit nicht erstellt. Verweise können nicht aktualisiert werden.**  
  
 Diese Umgestaltung Warnung ist nur verfügbar, für die Umgestaltung von Operationen, die bieten die **Vorschau der verweisänderungen** Option.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Fehlertolerante Umgestaltung und die Ergebnisse der Überprüfung  
 Umgestaltung ist fehlertolerant. Das heißt, können Sie ausführen, eine Umgestaltung in ein Projekt, das nicht erstellt werden kann. Allerdings kann in diesen Fällen die umgestaltungsprozess nicht mehrdeutige Verweise ordnungsgemäß aktualisiert werden.  
  
 Die **Ergebnisse der Überprüfung** Dialogfeld kann benachrichtigt, wenn die umgestaltungs-Engine Kompilierungsfehler erkennt oder erkennt, dass ein Umgestaltungsvorgang versehentlich führt dazu, einen Codeverweis dass sich an etwas anderes als den binden ursprünglich gebunden Sie (neubindung Problem).  
  
 Zum Aktivieren der Ergebnisse der Überprüfung feature, auf die **Tools** Menü klicken Sie auf **Optionen**. In der **Optionen** Dialogfeld erweitern Sie **Text-Editor**, und erweitern Sie dann **c#**. Klicken Sie auf **erweitert** , und wählen Sie die **Ergebnisse der Umgestaltung überprüfen** Kontrollkästchen.  
  
 Die **Ergebnisse der Überprüfung** Dialogfeld unterscheidet, den Unterschied zwischen zwei Arten von neubindung Probleme.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Verweise, dessen Definition nicht mehr das umbenannte Symbol ist.  
 Diese Art von das Problem tritt auf, wenn Sie ein Verweis auf ein Symbol umbenannt verweist nicht mehr. Beachten Sie z. B. folgenden Code:  
  
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
  
 Wenn Sie die Umgestaltung verwenden, um `a` zu `b`, dieses Dialogfeld wird angezeigt. Der Verweis auf die umbenannte Variable `a` nun bindet an den Parameter, der an den Konstruktor anstatt Bindung auf das Feld übergeben wird.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Verweise, deren Definition nun das umbenannte Symbol wird  
 Diese Art von das Problem tritt auf, wenn ein Verweis, der zuvor nicht auf das Symbol umbenannt jetzt auf das umbenannte Symbol verwiesen wird. Beachten Sie z. B. folgenden Code:  
  
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
  
 Wenn Sie die Umgestaltung verwenden, um `OtherMethod` zu `Method`, dieses Dialogfeld wird angezeigt. Der Verweis in `Main` verweist nun auf die überladene Methode, die akzeptiert eine `int` -Parameter, anstatt die überladene Methode, die akzeptiert eine `object` Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden die Visual Studio-Entwicklungsumgebung für c#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Gewusst wie: Wiederherstellen von C#-Refactoringausschnitten](../ide/how-to-restore-csharp-refactoring-snippets.md)