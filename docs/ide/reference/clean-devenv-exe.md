---
title: "/Clean (devenv.exe) | Microsoft Docs"
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
  - "/clean (Devenv-Schalter)"
  - "Builds [Team System], Bereinigen von Dateien"
  - "clean (Devenv-Schalter)"
  - "Devenv, /clean-Schalter"
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bereinigt alle temporären Dateien und Ausgabeverzeichnisse.  
  
## Syntax  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## Argumente  
 `FileName`  
 Erforderlich.  Der vollständige Pfad und Name der Projektmappendatei oder der Projektdatei.  
  
 \/project `ProjName`  
 Optional.  Der Pfad und Name einer Projektdatei innerhalb der Projektmappe.  Sie können einen relativen Pfad vom Ordner `SolutionName` zur Projektdatei, den Anzeigenamen des Projekts oder aber den vollständigen Pfad und Namen der Projektdatei angeben.  
  
 \/projectconfig `ProjConfigName`  
 Optional.  Der Name einer Projektbuildkonfiguration, die beim Bereinigen von `/project` verwendet werden soll.  
  
## Hinweise  
 Durch diesen Schalter wird dieselbe Funktion ausgeführt wie durch den Menübefehl **Projektmappe bereinigen** innerhalb der integrierten Entwicklungsumgebung \(IDE\).  
  
 Zeichenfolgen, die Leerzeichen enthalten, müssen in doppelte Anführungszeichen eingeschlossen werden.  
  
 Übersichtsinformationen für Bereinigungs\- und Buildvorgänge, einschließlich Fehler, können im **Befehlsfenster** oder in einer mit dem Schalter `/out` angegebenen Protokolldatei angezeigt werden.  
  
## Beispiel  
 Im ersten Beispiel wird die `MySolution`\-Projektmappe mithilfe der in der Projektmappendatei angegebenen Standardkonfiguration bereinigt.  
  
 Im zweiten Beispiel wird das Projekt `CSharpConsoleApp` unter Verwendung der `Debug`\-Projektbuildkonfiguration innerhalb der `Debug`\-Projektmappenkonfiguration von `MySolution` bereinigt.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)   
 [\/Build](../../ide/reference/build-devenv-exe.md)   
 [\/Rebuild](../../ide/reference/rebuild-devenv-exe.md)   
 [\/Out](../../ide/reference/out-devenv-exe.md)