---
title: "Befehl &quot;Disassemblierung auflisten&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.listdisassembly"
helpviewer_keywords: 
  - "Debug.ListDisassembly-Befehl"
  - "Disassembly auflisten (Befehl)"
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Befehl &quot;Disassemblierung auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Startet den Debugprozess und ermöglicht es, die Behandlungsweise von Fehlern festzulegen.  
  
## Syntax  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## Schalter  
 Jeder Schalter kann wahlweise über seine vollständige oder seine Kurzform aufgerufen werden.  
  
 \/count: `number` \[oder\] \/c: `number` \[oder\] \/length: `number` \[oder\] \/l: `number`  
 Optional.  Zahl der anzuzeigenden Anweisungen.  Der Standardwert ist 8.  
  
 \/endaddress: `expression` \[oder\] \/e: `expression`  
 Optional.  Adresse, an der die Disassembly angehalten werden soll.  
  
 \/codebytes:`yes`&#124;`no` \[oder\] \/bytes:`yes`&#124;`no` \[oder\] \/b:`yes`&#124;`no`  
 Optional.  Gibt an, ob Codebytes angezeigt werden sollen.  Der Standardwert lautet `no`.  
  
 \/source:`yes`&#124;`no` \[oder\] \/s:`yes`&#124;`no`  
 Optional.  Gibt an, ob Quellcode angezeigt werden soll.  Der Standardwert lautet `no`.  
  
 \/symbolnames:`yes`&#124;`no` \[oder\] \/names:`yes`&#124;`no` \[oder\] \/n:`yes`&#124;`no`  
 Optional.  Gibt an, ob Symbolnamen angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \[\/linenumbers:`yes`&#124;`no`\]  
 Optional.  Aktiviert die Anzeige von Zeilennummern, die dem Quellcode zugeordnet sind.  Der Schalter \/source muss den Wert `yes` aufweisen, damit der Schalter \/linenumbers verwendet werden kann.  
  
## Beispiel  
  
```  
>Debug.ListDisassembly  
```  
  
## Siehe auch  
 [Befehl "Aufrufliste auflisten"](../../ide/reference/list-call-stack-command.md)   
 [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)