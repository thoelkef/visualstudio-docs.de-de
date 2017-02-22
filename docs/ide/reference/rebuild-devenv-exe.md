---
title: "/Rebuild (devenv.exe) | Microsoft Docs"
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
  - "/rebuild (Devenv-Schalter)"
  - "Anwendungen [Visual Studio], Neuerstellen"
  - "Devenv, /rebuild-Schalter"
  - "Projekte [Visual Studio], Neuerstellen"
  - "rebuild (Devenv-Schalter)"
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bereinigt die angegebene Projektmappenkonfiguration und erstellt diese anschließend.  
  
## Syntax  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## Argumente  
 `SolnConfigName`  
 Erforderlich.  Der Name der Projektmappenkonfiguration, die zum Neuerstellen der in `SolutionName` benannten Projektmappe verwendet wird.  
  
 `SolutionName`  
 Erforderlich.  Der vollständige Pfad und Name der Projektmappendatei.  
  
 \/project `ProjName`  
 Dies ist optional.  Der Pfad und Name einer Projektdatei innerhalb der Projektmappe.  Sie können einen relativen Pfad vom Ordner `SolutionName` zur Projektdatei, den Anzeigenamen des Projekts oder aber den vollständigen Pfad und Namen der Projektdatei angeben.  
  
 \/projectconfig `ProjConfigName`  
 Dies ist optional.  Der Name einer Projektbuildkonfiguration, die beim Neuerstellen von `/project` verwendet werden soll.  
  
## Hinweise  
  
-   Durch diesen Schalter wird dieselbe Funktion ausgeführt wie durch den Menübefehl **Projektmappe neu erstellen** innerhalb der integrierten Entwicklungsumgebung \(IDE\).  
  
-   Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
-   Übersichtsinformationen für Bereinigungs\- und Buildvorgänge, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 In diesem Beispiel wird das Projekt `CSharpWinApp` unter Verwendung der `Debug`\-Projektbuildkonfiguration innerhalb der `Debug`\-Projektmappenkonfiguration von `MySolution` bereinigt und neu erstellt.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Clean](../../ide/reference/clean-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)