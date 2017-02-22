---
title: "/Build (devenv.exe) | Microsoft Docs"
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
  - "/build (Devenv-Schalter)"
  - "build (Devenv-Schalter)"
  - "Builds [Team System], Befehlszeile"
  - "Devenv, /build-Schalter"
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Build (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erstellt eine Projektmappe unter Verwendung einer angegebenen Projektmappenkonfigurationsdatei.  
  
## Syntax  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## Argumente  
 `SolutionName`  
 Erforderlich.  Der vollständige Pfad und Name der Projektmappendatei.  
  
 `SolnConfigName`  
 Erforderlich.  Der Name der Projektmappenkonfiguration, die zum Erstellen der in `SolutionName` benannten Projektmappe verwendet wird.  
  
 \/project `ProjName`  
 Optional.  Der Pfad und Name einer Projektdatei innerhalb der Projektmappe.  Sie können einen relativen Pfad vom Ordner `SolutionName` zur Projektdatei, den Anzeigenamen des Projekts oder aber den vollständigen Pfad und Namen der Projektdatei angeben.  
  
 \/projectconfig `ProjConfigName`  
 Optional.  Der Name einer Projektbuildkonfiguration, die beim Erstellen von `/project` verwendet werden soll.  
  
## Hinweise  
 Durch diesen Schalter wird dieselbe Funktion ausgeführt wie durch den Menübefehl **Projektmappe erstellen** innerhalb der integrierten Entwicklungsumgebung \(IDE\).  
  
 Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
 Übersichtsinformationen für Builds, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
 Mit diesem Befehl werden nur Projekte erstellt, die sich seit dem letzten Build geändert haben.  Um sämtliche Projekte in einer Projektmappe zu erstellen, verwenden Sie [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md).  
  
## Beispiel  
 In diesem Beispiel wird das Projekt `CSharpConsoleApp` unter Verwendung der `Debug`\-Projektbuildkonfiguration innerhalb der `Debug`\-Projektmappenkonfiguration von `MySolution` erstellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Siehe auch  
 [Erstellen und Bereinigen von Projekten und Projektmappen in Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)