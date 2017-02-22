---
title: "Befehl &quot;Aufrufliste auflisten&quot; | Microsoft Docs"
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
  - "debug.listcallstack"
helpviewer_keywords: 
  - "Debug.ListCallStack-Befehl"
  - "Aufrufliste auflisten (Befehl)"
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Aufrufliste auflisten&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zeigt die aktuelle Aufrufliste an.  
  
## Syntax  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## Argumente  
 `index`  
 Optional.  Legt den aktuellen Stapelrahmen fest und zeigt keine Ausgabe an.  
  
## Schalter  
 Jeder Schalter kann wahlweise über seine vollständige oder seine Kurzform aufgerufen werden.  
  
 \/Count:`number` \[oder\] \/C:`number`  
 Optional.  Maximale Anzahl der anzuzeigenden Aufruflisten.  Der Standardwert ist unbegrenzt.  
  
 \/ShowTypes:`yes`&#124;`no` \[oder\] \/T:`yes`&#124;`no`  
 Optional.  Gibt an, ob Parametertypen angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/ShowNames:`yes`&#124;`no` \[oder\] \/N:`yes`&#124;`no`  
 Optional.  Gibt an, ob Parameternamen angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/ShowValues:`yes`&#124;`no` \[oder\] \/V:`yes`&#124;`no`  
 Optional.  Gibt an, ob Parameterwerte angezeigt werden sollen.  Der Standardwert lautet `yes`.  
  
 \/ShowModule:`yes`&#124;`no` \[oder\] \/M:`yes`&#124;`no`  
 Optional.  Gibt an, ob der Modulname angezeigt werden soll.  Der Standardwert lautet `yes`.  
  
 \/ShowLineOffset:`yes`&#124;`no` \[oder\] \/\#:`yes`&#124;`no`  
 Optional.  Gibt an, ob das Zeilenoffset angezeigt werden soll.  Der Standardwert lautet `no`.  
  
 \/ShowByteOffset:`yes`&#124;`no` \[oder\] \/B:`yes`&#124;`no`  
 Optional.  Gibt an, ob das Byteoffset angezeigt werden soll.  Der Standardwert lautet `no`.  
  
 \/ShowLanguage:`yes`&#124;`no` \[oder\] \/L:`yes`&#124;`no`  
 Optional.  Gibt an, ob die Sprache angezeigt werden soll.  Der Standardwert lautet `no`.  
  
 \/IncludeCallsAcrossThreads:`yes`&#124;`no` \[oder\] \/I:`yes`&#124;`no`  
 Optional.  Gibt an, ob Aufrufe an andere Threads oder von anderen Threads mit eingeschlossen werden sollen.  Der Standardwert lautet `no`.  
  
 \/ShowExternalCode:`yes`&#124;`no`  
 Optional.  Gibt an, ob Nur mein Code für die Aufrufliste angezeigt werden soll.  Wenn Nur mein Code deaktiviert ist, wird der gesamte nicht benutzerseitige Code angezeigt.  Wenn Nur mein Code aktiviert ist, wird nicht benutzerseitiger Code in der Ausgabe der Aufrufliste als `[external]` angezeigt.  
  
 Thread:`n`  
 Optional.  Zeigt die Aufrufliste für Thread `n` an.  Wenn kein Thread angegeben ist, wird die Aufrufliste für den aktuellen Thread angezeigt.  
  
## Hinweise  
 Änderungen an den Argumenten oder Schaltern wirken sich auf spätere Aufrufe dieses Befehls aus.  Wenn Sie `Debug.ListCallStack`  allein ausgeben, wird die gesamte Aufrufliste angezeigt.  Wenn Sie einen Index wie  
  
```  
Debug.ListCallStack 2  
```  
  
 angeben, wird der aktuelle Stapelrahmen auf diesen Rahmen festgelegt \(in diesem Fall der zweite Rahmen\).  
  
 Sie können diesen Befehl auch mithilfe seines vordefinierten Aliases kb schreiben.  Beispielsweise können Sie  
  
```  
kb 2  
```  
  
 eingeben, um den aktuellen Stapelrahmen auf den zweiten Rahmen festzulegen.  
  
## Beispiel  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## Siehe auch  
 [Befehl "Disassemblierung auflisten"](../../ide/reference/list-disassembly-command.md)   
 [Befehl "Threads auflisten"](../../ide/reference/list-threads-command.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)