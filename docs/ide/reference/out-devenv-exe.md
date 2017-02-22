---
title: "/Out (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/out (Devenv-Schalter)"
  - "Builds [Visual Studio], Fehler"
  - "Builds [Visual Studio], Protokolle"
  - "Devenv, /out-Schalter"
  - "Fehlerprotokolle [Visual Studio]"
  - "Fehlerprotokolle [Visual Studio], Fehler beim Erstellen über die Befehlszeile"
  - "Fehler [Visual Studio], Builds"
  - "out (Devenv-Schalter)"
  - "Ausgabedateien, Buildfehler"
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Out (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt eine Datei zum Speichern und für die Anzeige von Fehlern fest, die beim Ausführen, Erstellen, Neuerstellen oder Bereitstellen einer Projektmappe ausgegeben werden.  
  
## Syntax  
  
```  
devenv /out FileName  
```  
  
## Argumente  
 `FileName`  
 Erforderlich.  Der Pfad und der Name der Datei, der bzw. die Fehler beim Erstellen einer ausführbaren Datei aufnimmt.  
  
## Hinweise  
 Wenn der Name einer nicht vorhandenen Datei angegeben wird, wird die entsprechende Datei automatisch erstellt.  Wenn die Datei bereits vorhanden ist, werden die Ergebnisse an den vorhandenen Inhalt der Datei angefügt.  
  
 Während eines Befehlszeilenbuilds aufgetretene Fehler werden im **Befehlsfenster** und in der Ansicht Projektmappen\-Generator des **Ausgabefensters** angezeigt.  Diese Option ist nützlich, wenn Sie unbeaufsichtigte Builds erstellen und die Ergebnisse anzeigen können müssen.  
  
## Beispiel  
 In diesem Beispiel wird `MySolution` ausgeführt und Fehler in die Datei `MyErrorLog.txt` geschrieben.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)