---
title: Codeausschnitte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e28ebd46a03983e60ebdd3fc22dd55d85249f710
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188856"
---
# <a name="code-snippets"></a>Codeausschnitte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Codeausschnitte sind kleine Blöcke mit wiederverwendbarem Code, die in einer Codedatei über einen Befehl im Kontextmenü oder eine Kombination von Hotkeys eingefügt werden können. Sie enthalten normalerweise häufig verwendete Codeblöcke, wie z. B. Try-finally- oder If-else-Blöcke, können aber zum Einfügen von ganze Klassen oder Methoden verwendet werden.  
  
## <a name="expansion-snippets-and-surround-with-snippets"></a>Erweiterungsausschnitte und umschließende Ausschnitte  
 In Visual Studio gibt es zwei Arten von Codeausschnitten: Erweiterungsausschnitte, die an einer angegebenen Einfügemarke hinzugefügt werden und eine Ausschnittsverknüpfung ersetzen können, und umschließende Ausschnitte (nur in C# und C++), die um einen ausgewählten Codeblock herum eingefügt werden.  
  
 Ein Beispiel für einen Einfügungsausschnitt: In C# wird die Verknüpfung Tryf verwendet, um einen Try-finally-Block einzufügen:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Sie können diesen Ausschnitt einfügen, indem Sie auf **Ausschnitt einfügen** im Kontextmenü des Codefensters klicken, dann auf **Visual C#** klicken, `tryf` eingeben und dann die Tabstopptaste drücken, oder Sie können `tryf` eingeben und dann zweimal die Tabstopptaste drücken.  
  
 Ein Beispiel für einen Umschließungsausschnitt: In C++ kann die Verknüpfung `if` als Einfügungsausschnitt oder als Umschließungsausschnitt verwendet werden. Wenn Sie eine Codezeile aktivieren (z.B. `return FALSE;`) und dann auf **Umschließen mit** und auf **if**klicken, wird der Ausschnitt um folgende Zeile erweitert:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## <a name="snippet-replacement-parameters"></a>Ersatzparameter für Ausschnitte  
 Ausschnitte können Ersatzparameter enthalten, die Platzhalter sind und ersetzt werden müssen, um genau den Code anzupassen, den Sie schreiben. Im vorherigen Beispiel ist `true` ein Ersatzparameter, den Sie durch die entsprechende Bedingung ersetzen. Diese Ersetzung wird für jede Instanz des Ersatzparameters im Ausschnitt wiederholt.  
  
 In Visual Basic gibt es z. B. ein Codeausschnitt, der eine Eigenschaft einfügt. Klicken Sie im Kontextmenü des Codefensters auf **Ausschnitt einfügen**, dann auf **Codemuster**, dann auf **Eigenschaften, Prozeduren, Ereignisse**, und definieren dann eine Eigenschaft. Der folgende Code wird eingefügt:  
  
```  
Private newPropertyValue As String  
Public Property NewProperty() As String  
    Get  
        Return newPropertyValue  
    End Get  
    Set(ByVal value As String)  
        newPropertyValue = value  
    End Set  
End Property  
  
```  
  
 Wenn Sie `newPropertyValue` in `m_property` ändern, wird jede Instanz von `newPropertyValue` geändert. Wenn Sie `String` in der Eigenschaftendeklaration in `Int` ändern, wird der Wert in der set-Methode ebenfalls in `Int` geändert.  
  
## <a name="code-snippet-manager"></a>Codeausschnitt-Manager  
 Sie zeigen alle derzeit installierten Codeausschnitte sowie deren Speicherort auf dem Datenträger an, indem Sie auf **Tools/Codeausschnitt-Manager** klicken. Ausschnitte werden je nach Sprache angezeigt.  
  
 Sie können Ausschnittverzeichnisse mit den Schaltflächen **Hinzufügen** und **Entfernen** im Dialogfeld **Codeausschnitt-Manager** hinzufügen und entfernen. Verwenden Sie zum Hinzufügen einzelner Codeausschnitte die Schaltfläche **Importieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md)   
 [Vorgehensweise: Verteilen von Codeausschnitten](../ide/how-to-distribute-code-snippets.md)   
 [Empfohlene Vorgehensweisen für die Verwendung von Codeausschnitten](../ide/best-practices-for-using-code-snippets.md)   
 [Problembehandlung bei Codeausschnitten](../ide/troubleshooting-snippets.md)   
 [Visual C#-Codeausschnitte](../ide/visual-csharp-code-snippets.md)   
 [Visual C++-Codeausschnitte](../ide/visual-cpp-code-snippets.md)   
 [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md)
