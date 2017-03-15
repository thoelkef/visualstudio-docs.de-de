---
title: "/ProjectConfig (devenv.exe) | Microsoft Docs"
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
  - "/projectconfig (Devenv-Schalter)"
  - "Buildkonfigurationen, Angeben"
  - "Konfigurationen, Bereinigen"
  - "Konfigurationen, Neuerstellen"
  - "Bereitstellungsprojekte, Hinzufügen"
  - "Bereitstellungsprojekte, Erstellen"
  - "Bereitstellungsprojekte, Angeben"
  - "Devenv, /projectconfig-Schalter"
  - "projectconfig (Devenv-Schalter)"
  - "Projekte [Visual Studio], Buildkonfiguration"
  - "Projekte [Visual Studio], Bereinigen"
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt eine Projektbuildkonfiguration fest, die für das im `/project`\-Argument angegebene Projekt übernommen werden soll, wenn Sie dieses erstellen, bereinigen, neu erstellen oder bereitstellen.  
  
## Syntax  
  
```  
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
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
  
-   Muss als Bestandteil der Befehle `devenv /build`, \/`clean`, `/rebuild` oder `/deploy` zusammen mit dem Schalter `/project` verwendet werden.  
  
-   Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
-   Übersichtsinformationen für Builds, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` unter Verwendung der `Debug`\-Projektbuildkonfiguration innerhalb der `Debug`\-Projektmappenkonfiguration von `MySolution` erstellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Deploy](../../ide/reference/deploy-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)