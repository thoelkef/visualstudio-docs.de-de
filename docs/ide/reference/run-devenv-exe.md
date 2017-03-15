---
title: "/Run (devenv.exe) | Microsoft Docs"
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
  - "/r (Devenv-Schalter)"
  - "/run (Devenv-Schalter)"
  - "Anwendungen [Visual Studio], Ausführen"
  - "Devenv, /run-Schalter"
  - "r (Devenv-Schalter)"
  - "run (Devenv-Schalter)"
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Run (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt es bzw. sie aus.  
  
## Syntax  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## Argumente  
 `SolutionName`  
 Erforderlich.  Der vollständige Pfad und Name einer Projektmappendatei.  
  
 `ProjectName`  
 Erforderlich.  Der vollständige Pfad und Name einer Projektdatei.  
  
## Hinweise  
 Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt dieses\/diese anschließend aus, entsprechend den für die aktuelle Projektmappenkonfiguration festgelegten Einstellungen.  Dieser Schalter startet die integrierte Entwicklungsumgebung \(IDE\) und lässt sie aktiviert, nachdem die Ausführung des Projekts oder der Projektmappe beendet ist.  
  
-   Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
-   Übersichtsinformationen, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 In diesem Beispiel wird die Projektmappe `MySolution` unter Verwendung der aktiven Bereitstellungskonfiguration ausgeführt.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Runexit](../../ide/reference/runexit-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)