---
title: "/Project (devenv.exe) | Microsoft Docs"
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
  - "/project (Devenv-Schalter)"
  - "Bereitstellungsprojekte, Angeben"
  - "Devenv, /project-Schalter"
  - "project (Devenv-Schalter)"
  - "Projekte [Visual Studio], Erstellen"
  - "Projekte [Visual Studio], Bereinigen"
  - "Projekte [Visual Studio], Neuerstellen"
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Project (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Identifiziert innerhalb der angegebenen Projektmappenkonfiguration ein einzelnes Projekt zur Erstellung, Bereinigung, Neuerstellung oder Bereitstellung.  
  
## Syntax  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName   
[/project ProjName] [/projectconfig ProjConfigName]   
```  
  
## Argumente  
 \/build  
 Erstellt das durch `/project` `ProjName` angegebene Projekt.  
  
 \/clean  
 Bereinigt alle während des Erstellens erstellten temporären Dateien und Ausgabeverzeichnisse.  
  
 \/rebuild  
 Bereinigt das durch `/project` `ProjName` angegebene Projekt und erstellt es anschließend.  
  
 \/deploy  
 Gibt an, dass das Projekt nach dem Erstellen oder Neuerstellen bereitgestellt werden soll.  
  
 `SolnConfigName`  
 Erforderlich.  Der Name der Projektmappenkonfiguration, die für die in `SolutionName` angegebene Projektmappe übernommen werden soll.  
  
 `SolutionName`  
 Erforderlich.  Der vollständige Pfad und Name der Projektmappendatei.  
  
 \/project `ProjName`  
 Optional.  Der Pfad und Name einer Projektdatei innerhalb der Projektmappe.  Sie können einen relativen Pfad vom Ordner `SolutionName` zur Projektdatei, den Anzeigenamen des Projekts oder aber den vollständigen Pfad und Namen der Projektdatei angeben.  
  
 \/projectconfig `ProjConfigName`  
 Optional.  Der Name einer Projektbuildkonfiguration, die für `/project` übernommen werden soll.  
  
## Hinweise  
  
-   Muss als Bestandteil der Befehle `devenv /build`, \/`clean`, `/rebuild` oder `/deploy` verwendet werden.  
  
-   Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
-   Übersichtsinformationen für Builds, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` unter Verwendung der `Debug`\-Projektbuildkonfiguration innerhalb der `Debug`\-Projektmappenkonfiguration von `MySolution` erstellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/ProjectConfig](../../ide/reference/projectconfig-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)