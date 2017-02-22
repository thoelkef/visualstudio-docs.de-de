---
title: "Sicherheitswarnung: Der Debugger muss diesen nicht vertrauensw&#252;rdigen Befehl ausf&#252;hren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.sourceserver.securityalert"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sicherheitswarnung: Der Debugger muss diesen nicht vertrauensw&#252;rdigen Befehl ausf&#252;hren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Warnmeldung wird bei Verwendung des Quellservers angezeigt.  Diese Meldung besagt, dass der Befehl, den der Debugger zum Abrufen von Quellcode ausführen muss, nicht in der Liste der vertrauenswürdigen Befehle für Quellserver in der Datei "srcsvr.ini" aufgeführt ist.  Wenn dies ein gültiger Befehl ist, können Sie ihn der Datei "srcsvr.ini" hinzufügen.  Andernfalls sollten Sie ihn nicht ausführen.  Weitere Informationen finden Sie unter [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## Meldungstext  
 Der Debugger muss den folgenden nicht vertrauenswürdigen Befehl ausführen, um Quellcode vom Quellserver abzurufen.  
  
 Wenn die Debugsymboldatei \(\*.pdb\) nicht aus einer bekannten und vertrauenswürdigen Quelle stammt, ist dieser Befehl möglicherweise ungültig oder kann nicht sicher ausgeführt werden.  
  
 Möchten Sie diesen Befehl ausführen?  
  
## UIElement-Liste  
 Textfeld  
 Auszuführender Befehl aus der PDB\-Datei.  
  
 Run  
 Lässt die Ausführung des Befehls zu.  
  
 Nicht ausführen  
 Beendet die Ausführung des Befehls und das Herunterladen der Datei vom Quellserver.  
  
## Siehe auch  
 [Angeben von Symbol\(PDB\)\- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Quellserver](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)