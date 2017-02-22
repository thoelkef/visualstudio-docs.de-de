---
title: "/Runexit (devenv.exe) | Microsoft Docs"
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
  - "/runexit (Devenv-Schalter)"
  - "Devenv, /runexit-Schalter"
  - "runexit (Devenv-Schalter)"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt es bzw. sie aus. Anschließend wird die integrierte Entwicklungsumgebung \(IDE\) geschlossen.  
  
## Syntax  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## Argumente  
 `SolutionName`  
 Erforderlich.  Der vollständige Pfad und Name einer Projektmappendatei.  
  
 `ProjectName`  
 Erforderlich.  Der vollständige Pfad und Name einer Projektdatei.  
  
## Hinweise  
 Kompiliert das angegebene Projekt oder die angegebene Projektmappe und führt dieses\/diese anschließend aus, entsprechend den für die aktuelle Projektmappenkonfiguration festgelegten Einstellungen.  Dieser Schalter minimiert die IDE während der Ausführung des Projekts oder der Projektmappe und schließt die IDE, nachdem die Ausführung des Projekts oder der Projektmappe abgeschlossen ist.  
  
-   Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
-   Übersichtsinformationen, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 In diesem Beispiel wird die Projektmappe `MySolution` in der minimierten IDE unter Verwendung der aktiven Bereitstellungskonfiguration ausgeführt und die IDE anschließend geschlossen.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Run](../../ide/reference/run-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)