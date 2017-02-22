---
title: "/Edit (devenv.exe) | Microsoft Docs"
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
  - "/Edit (Devenv-Schalter)"
  - "Devenv, /edit-Schalter"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet die angegebene Datei in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntax  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## Argumente  
 `file1`  
 Optional.  Die Datei, die in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet werden soll.  Wenn keine Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vorhanden ist, wird eine neue Instanz mit einem vereinfachten Fensterlayout erstellt und `file1` in der neuen Instanz geöffnet.  
  
 `file2`  
 Optional.  Eine oder mehrere weitere Dateien, die in der vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet werden sollen.  
  
## Hinweise  
 Wenn keine Datei angegeben wurde und eine Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vorhanden ist, erhält die vorhandene Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Fokus.  Wenn keine Datei angegeben wurde und keine Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vorhanden ist, wird eine neue Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mit einem vereinfachten Fensterlayout erstellt.  
  
 Wenn sich die vorhandene Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in einem modalen Zustand befindet, z. B. wenn das [Dialogfeld Optionen](../../ide/reference/options-dialog-box-visual-studio.md) geöffnet ist, wird die Datei in der vorhandenen Instanz geöffnet, sobald [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den modalen Zustand verlässt.  
  
## Beispiel  
 Dieses Beispiel öffnet die Datei `MyFile.cs` in einer vorhandenen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oder, falls noch keine vorhanden ist, in einer neuen Instanz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
```  
devenv /edit MyFile.cs  
```  
  
## Siehe auch  
 [Devenv\-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)