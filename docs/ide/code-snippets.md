---
title: "Codeausschnitte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.ExpansionManagerImport"
  - "vs.codesnippetmanager"
helpviewer_keywords: 
  - "Codeausschnitte"
  - "Codeausschnitte, Erweiterung"
  - "Codeausschnitte, Ersetzungsparameter"
  - "Codeausschnitte, Umschließen mit"
  - "Ersetzungsparameter"
  - "Umschließen mit"
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Codeausschnitte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Codeausschnitte sind kleine Blöcke mit wiederverwendbarem Code, die in einer Codedatei über einen Befehl im Kontextmenü oder eine Kombination von Hotkeys eingefügt werden können.  Sie enthalten normalerweise häufig verwendete Codeblöcke, wie z. B. Try\-finally\- oder If\-else\-Blöcke, können aber zum Einfügen von ganze Klassen oder Methoden verwendet werden.  
  
## Erweiterungsausschnitte und umschließende Ausschnitte  
 In Visual Studio gibt es zwei Arten von Codeausschnitten: Erweiterungsausschnitte, die an einer angegebenen Einfügemarke hinzugefügt werden und eine Ausschnittsverknüpfung ersetzen können, und umschließende Ausschnitte \(nur in C\# und C\+\+\), die um einen ausgewählten Codeblock herum eingefügt werden.  
  
 Ein Beispiel für einen Einfügungsausschnitt: In C\# wird die Verknüpfung Tryf verwendet, um einen Try\-finally\-Block einzufügen:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Sie können diesen Ausschnitt einfügen, indem Sie auf **Ausschnitt einfügen** im Kontextmenü des Codefensters klicken, dann auf **Visual C\#** klicken, `tryf` eingeben und dann die TAB\-Taste drücken, oder Sie können `tryf` eingeben und dann TAB \+ TAB drücken.  
  
 Ein Beispiel für einen Umschließungsausschnitt: In C\+\+ kann die Verknüpfung `if` als Einfügungsausschnitt oder als Umschließungsausschnitt verwendet werden.  Wenn Sie eine Codezeile aktivieren \(z. B. `return FALSE;`\) und dann auf **Umschließen mit** und auf **if** klicken, wird der Ausschnitt um folgende Zeile erweitert:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## Ersatzparameter für Ausschnitte  
 Ausschnitte können Ersatzparameter enthalten, die Platzhalter sind und ersetzt werden müssen, um genau den Code anzupassen, den Sie schreiben.  Im vorherigen Beispiel ist `true` ein Ersatzparameter, den Sie durch die entsprechende Bedingung ersetzen.  Diese Ersetzung wird für jede Instanz des Ersatzparameters im Ausschnitt wiederholt.  
  
 In Visual Basic gibt es z. B. ein Codeausschnitt, der eine Eigenschaft einfügt.  Klicken Sie auf **Ausschnitt einfügen** im Kontextmenü des Codefensters, dann auf **Codemuster**, dann auf **Eigenschaften, Prozeduren, Ereignisse**, und definieren Sie dann eine Eigenschaft.  Der folgende Code wird eingefügt:  
  
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
  
 Wenn Sie `newPropertyValue` in `m_property` ändern, wird jede Instanz von `newPropertyValue` geändert.  Wenn Sie `String` in der Eigenschaftendeklaration in `Int` ändern, wird der Wert in der set\-Methode ebenfalls in `Int` geändert.  
  
## Codeausschnitt\-Manager  
 Sie zeigen alle derzeit installierten Codeausschnitte sowie deren Speicherort auf dem Datenträger an, indem Sie auf **Tools\/Codeausschnitt\-Manager** klicken.  Ausschnitte werden je nach Sprache angezeigt.  
  
 Sie können Ausschnittverzeichnisse mit den Schaltflächen **Hinzufügen** und **Entfernen** im Dialogfeld **Codeausschnitt\-Manager** hinzufügen und entfernen.  Verwenden Sie zum Hinzufügen einzelner Codeausschnitte die Schaltfläche **Importieren**.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen eines Codeausschnitts](../ide/walkthrough-creating-a-code-snippet.md)   
 [Gewusst wie: Verteilen von Codeausschnitten](../ide/how-to-distribute-code-snippets.md)   
 [Empfohlene Vorgehensweisen für die Verwendung von Codeausschnitten](../ide/best-practices-for-using-code-snippets.md)   
 [Problembehandlung bei Codeausschnitten](../ide/troubleshooting-snippets.md)   
 [Visual C\#\-Codeausschnitte](../ide/visual-csharp-code-snippets.md)   
 [Visual C\+\+\-Codeausschnitte](../ide/visual-cpp-code-snippets.md)   
 [Schemareferenz für Codeausschnitte](../ide/code-snippets-schema-reference.md)