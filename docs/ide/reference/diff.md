---
title: "/Diff | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Diff
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vergleicht zwei Dateien.  Die Unterschiede werden in einem bestimmten von Visual Studio angezeigt.  
  
## Syntax  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],  
[TargetDisplayName]  
```  
  
## Argumente  
 `SourceFile`  
 Erforderlich.  Der vollständige Pfad und Name der ersten zu vergleichende Datei.  
  
 `TargetFile`  
 Erforderlich.  Der vollständige Pfad und Name der zweiten zu vergleichende Datei  
  
 `SourceDisplayName`  
 Dies ist optional.  Der Anzeigename der ersten Datei.  
  
 `TargetDisplayName`  
 Dies ist optional.  Der Anzeigename der zweiten Datei.