---
title: "/Deploy (devenv.exe) | Microsoft Docs"
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
  - "/deploy (Devenv-Schalter)"
  - "deploy (Devenv-Schalter)"
  - "Bereitstellen von Anwendungen [Visual Studio], Nach dem Erstellen"
  - "Devenv, /deploy-Schalter"
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt eine Projektmappe nach einer Erstellung oder Neuerstellung bereit.  Gilt nur für Projekte mit verwaltetem Code.  
  
## Syntax  
  
```  
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]  
```  
  
## Argumente  
 `SolnConfigName`  
 Erforderlich.  Der Name der Projektmappenkonfiguration, die zum Erstellen der in `SolutionName` benannten Projektmappe verwendet wird.  
  
 `SolutionName`  
 Erforderlich.  Der vollständige Pfad und Name der Projektmappendatei.  
  
 \/project `ProjName`  
 Optional.  Der Pfad und Name einer Projektdatei innerhalb der Projektmappe.  Sie können einen relativen Pfad vom Ordner `SolutionName` zur Projektdatei, den Anzeigenamen des Projekts oder aber den vollständigen Pfad und Namen der Projektdatei angeben.  
  
 \/projectconfig `ProjConfigName`  
 Optional.  Der Name einer Projektbuildkonfiguration, die beim Erstellen von `/project` verwendet werden soll.  
  
## Hinweise  
 Bei dem angegebenen Projekt muss es sich um ein Bereitstellungsprojekt handeln.  Ist das Projekt kein Bereitstellungsprojekt, schlägt es mit Ausgabe eines Fehlers fehl, wenn es für die Bereitstellung übergeben wird.  
  
 Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
 Übersichtsinformationen für Builds, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` unter Verwendung der `Release`\-Projektbuildkonfiguration innerhalb der `Release`\-Projektmappenkonfiguration von `MySolution` bereitgestellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release   
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Project](../../ide/reference/project-devenv-exe.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)