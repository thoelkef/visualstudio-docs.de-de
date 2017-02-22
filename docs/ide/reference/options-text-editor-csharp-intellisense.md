---
title: "Optionen, Text-Editor, C#, IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense"
helpviewer_keywords: 
  - "IntelliSense [J#], Optionen"
  - "Unterstreichungen, wellenförmige"
  - "IntelliSense [C#], Optionen"
  - "IntelliSense [c#], wellenförmige Unterstreichungen"
  - "Wellenförmige Unterstreichungen"
  - "Text-Editor-Optionen (Dialogfeld), IntelliSense"
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Optionen, Text-Editor, C#, IntelliSense
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Eigenschaftenseite **IntelliSense**, um Einstellungen zu ändern, die das Verhalten von IntelliSense für Visual C\# beeinflussen.  Sie greifen auf die Eigenschaftenseite **IntelliSense** zu, indem Sie im Menü **Extras** auf **Optionen** und dann im Ordner **Text\-Editor** auf **C\#** und schließlich auf **IntelliSense** klicken.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Die Eigenschaftenseite **IntelliSense** enthält die folgenden Eigenschaften:  
  
## Vervollständigungslisten  
 **Vervollständigungsliste nach Eingabe des ersten Zeichens anzeigen**  
 Bei Auswahl dieser Option zeigt IntelliSense die Vervollständigungsliste automatisch an, wenn Sie mit der Eingabe beginnen.  Wenn diese Option nicht aktiviert ist, kann die IntelliSense\-Vervollständigung weiterhin über das Menü **IntelliSense** oder durch Drücken von STRG\+LEERTASTE aktiviert werden.  
  
 **Schlüsselwörter in Vervollständigungslisten platzieren**  
 Bei Auswahl dieser Option fügt IntelliSense C\#\-Schlüsselwörter \(z. B. [Klasse](/dotnet/csharp/language-reference/keywords/class)\) in die Vervollständigungsliste ein.  
  
 **Codeausschnitte in Vervollständigungslisten platzieren**  
 Bei Auswahl dieser Option fügt IntelliSense Aliase für C\#\-Codeausschnitte in die Vervollständigungsliste ein.  Wenn der Alias für den Codeausschnitt mit einem Schlüsselwort übereinstimmt \(z. B. [Klasse](/dotnet/csharp/language-reference/keywords/class)\), wird das Schlüsselwort durch die Verknüpfung ersetzt.  Weitere Informationen finden Sie unter [Visual C\#\-Codeausschnitte](../../ide/visual-csharp-code-snippets.md).  
  
## Auswahl in Vervollständigungslisten  
 **Commit bei Eingabe der folgenden Zeichen:**  
 Gibt alle Zeichen an, nach deren Eingabe die automatische IntelliSense\-Vervollständigung für das ausgewählte Element in der Vervollständigungsliste ausgeführt wird.  
  
 **Commit beim Drücken der Leertaste**  
 Gibt an, dass das Drücken der Leertaste als Aktion gilt, durch die die automatische IntelliSense\-Vervollständigung für das ausgewählte Element in der Vervollständigungsliste ausgeführt wird.  
  
 **Bei Eingabe neue Zeile nach jedem ganzen Wort hinzufügen**  
 Gibt an, dass nach vollständiger Eingabe eines Eintrags in der Vervollständigungsliste und anschließendem Drücken der EINGABETASTE automatisch eine neue Zeile erstellt und der Cursor in die neue Zeile gesetzt wird.  
  
 Wenn Sie z. B. `else` eingegeben und anschließend die EINGABETASTE drücken, wird im Editor Folgendes angezeigt:  
  
 `else`  
  
 `|` \(Cursorposition\)  
  
 Wenn Sie jedoch lediglich `el` eingegeben und anschließend die EINGABETASTE drücken, wird im Editor Folgendes angezeigt:  
  
 `else|` \(Cursorposition\)  
  
## IntelliSense\-Memberauswahl  
 **Wählt den zuletzt verwendeten Member vorab aus.**  
 Wenn diese Option ausgewählt ist, eine IntelliSense Vorauswahl unter die Membern, die Sie vor kurzem in der Pop\-Up Feld Member auflisten für automatische Vervollständigung von Objektnamen während der aktuellen Sitzung in der integrierten Entwicklungsumgebung \(IDE\) ausgewählt haben.  Der Verlauf zuletzt verwendeter Member wird zwischen den einzelnen IDE\-Sitzungen gelöscht.  Weitere Informationen finden Sie unter [IntelliSense für die zuletzt verwendeten Member](../../misc/intellisense-for-most-recently-used-members.md).  
  
## Siehe auch  
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML\-Dokumentationskommentare](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)