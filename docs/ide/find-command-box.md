---
title: "Such/Befehlsfeld | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findcommandbox"
helpviewer_keywords: 
  - "Suchen (Feld)"
ms.assetid: c81736dd-7a26-4e11-95c8-c2a2e56d7a41
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Such/Befehlsfeld
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können nach Text suchen und Visual Studio\-Befehle vom **Such\-\/Befehlsfeld** ausführen.  Das Feld **Suchen\/Befehl** ist als Symbolleisten\-Steuerelement weiterhin verfügbar, jedoch nicht mehr standardmäßig sichtbar.  Sie können das Feld **Suchen\/Befehl** anzeigen, indem Sie auf der Symbolleiste **Standard** die Option **Schaltflächen hinzufügen oder entfernen** und dann **Suchen** auswählen.  
  
 Um einen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Befehl auszuführen, leiten Sie ihn mit einem Größer\-als\-Zeichen \(\>\) ein.  
  
 Das **Such\-\/Befehlsfeld** behält die letzten 20 Einträge bei, und zeigt diese in einer Dropdownliste an.  Mithilfe der Pfeiltasten kann in der Liste navigiert werden.  
  
 ![Such&#47;Befehlsfeld](../ide/media/findcommandbox.png "FindCommandBox")  
Such\-\/Befehlsfeld  
  
## Nach Text suchen  
 Wenn Sie Text im **Such\-\/Befehlsfeld** angeben und dann die EINGABETASTE drücken, durchsucht Visual Studio standardmäßig das aktuelle Dokument oder das Toolfenster unter Anwendung der Optionen, die im Dialogfeld **In Dateien suchen** festgelegt wurden.  Weitere Informationen finden Sie unter [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md).  
  
## Eingeben von Befehlen  
 Um das **Such\-\/Befehlsfeld** zum Ausgeben eines einzelnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Befehls oder \-Alias anstatt zur Textsuche zu verwenden, geben Sie den gewünschten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Befehl mit einem vorangestellten Größer\-als\-Zeichen \(\>\) ein.  Beispiel:  
  
```  
>File.NewFile c:\temp\MyFile /t:"General\Text File"  
```  
  
 Darüber hinaus können Sie auch das Befehlsfenster zum Eingeben und Ausführen von einzelnen oder mehreren Befehlen verwenden.  Einige Befehle oder Aliase können eigenständig eingegeben und ausgeführt werden, für andere erfordert die Syntax die Angabe von Argumenten.  Eine Liste mit Befehlen, die über Argumente verfügen, finden Sie unter [Visual Studio\-Befehle](../ide/reference/visual-studio-commands.md).  
  
## Escapezeichen  
 Ein Caretzeichen \(^\) in einer Befehlszeile bedeutet, dass das unmittelbar darauf folgende Zeichen literal und nicht als Steuerzeichen interpretiert wird.  Dies ermöglicht das Einbetten von geraden Anführungszeichen \("\), Leerzeichen, vorangestellten Schrägstrichen, Caretzeichen oder beliebigen anderen Literalzeichen in einen Parameter\- oder Schalterwert, mit Ausnahme von Schalternamen.  Beispiel:  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Die Funktionsweise des Caretzeichens ist unabhängig davon, ob es in Anführungszeichen eingeschlossen ist oder nicht.  Wenn ein Caretzeichen das letzte Zeichen in einer Zeile ist, wird es ignoriert.  
  
## Siehe auch  
 [Befehlsfenster](../ide/reference/command-window.md)   
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)