---
title: "/Upgrade (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/upgrade (Devenv-Schalter)"
  - "Devenv, /upgrade-Schalter"
  - "upgrade (Devenv-Schalter)"
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Aktualisiert die Projektmappendatei und alle zugehörigen Projektdateien bzw. die angegebene Projektdatei mit den aktuellen , für diese Dateien gültigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Formaten.  
  
## Syntax  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## Argumente  
 `SolutionFile`  
 Dies ist erforderlich, sofern Sie eine vollständige Projektmappe und deren Projekte aktualisieren.  Der Pfad und Name einer Projektmappendatei.  Es reicht aus, nur den Namen der Projektmappendatei oder einen vollständigen Pfad und den Namen der Projektmappendatei einzugeben.  Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.  
  
 `ProjectFile`  
 Dies ist erforderlich, sofern Sie ein einzelnes Projekt aktualisieren.  Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe.  Es reicht aus, nur den Namen der Projektdatei oder einen vollständigen Pfad und den Namen der Projektdatei einzugeben.  Wenn der angegebene Ordner bzw. die Datei noch nicht vorhanden ist, wird der Ordner oder die Datei erstellt.  
  
## Hinweise  
 Es werden automatisch Sicherungen und in ein Verzeichnis mit der Bezeichnung "Backup" kopiert, das im aktuellen Verzeichnis erstellt wurde.  
  
 Der Quellcodeverwaltung unterliegende Projektmappen oder Projekte müssen ausgecheckt werden, bevor sie aktualisiert werden können.  
  
 Bei Verwendung des Schalters `/upgrade` wird [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nicht gestartet.  Die Ergebnisse des Upgrades sind im Upgradebericht für die Entwicklungssprache der Projektmappe oder des Projekts aufgeführt.  Informationen zu Fehlern oder zur Verwendung werden nicht zurückgegeben.  Weitere Informationen über das Aktualisieren von Projekten in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] finden Sie unter [Gewusst wie: Problembehandlung bei nicht erfolgreichen Visual Studio\-Projektupgrades](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## Beispiel  
 In diesem Beispiel wird eine Projektmappendatei mit dem Namen "MyProject.sln" im Standardordner für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]\-Projektmappen aktualisiert.  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## Siehe auch  
 [Gewusst wie: Problembehandlung bei nicht erfolgreichen Visual Studio\-Projektupgrades](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)