---
title: "Projekttyp nicht verf&#252;gbar. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projecttypenotavailable"
helpviewer_keywords: 
  - "Projekttyp nicht verfügbar (Fehler)."
ms.assetid: a579fe75-efa2-4dd0-b5d7-ae106d3aedbd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Projekttyp nicht verf&#252;gbar.
In diesem Dialogfeld wird folgende Fehlermeldung angezeigt: "Das Projekt \<Projekt\> kann nicht geöffnet werden, weil der Projekttyp \<Projekttyp\> von dieser Version der Anwendung nicht unterstützt wird."  
  
## Problemumgehung  
  
-   Dieses Dialogfeld wird angezeigt, da das zum Öffnen der angegebenen Datei erforderliche Produkt bzw. die erforderliche Produktversion nicht gefunden wurde.  Dieser Fehler tritt im Allgemeinen auf, wenn versucht wird, eine Projektdatei zu öffnen, die mit der installierten Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht geöffnet werden kann.  Wenn Sie beispielsweise versuchen, eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Projektdatei mit [!INCLUDE[vbprvbxprlong](../misc/includes/vbprvbxprlong_md.md)] zu öffnen, wird dieses Dialogfeld angezeigt.  
  
#### So umgehen Sie diesen Fehler  
  
-   Installieren Sie die richtige Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Siehe auch  
 [Portieren, Migrieren und Aktualisieren von Visual Studio\-Projekten](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Projekteigenschaftenverweise](../ide/reference/project-properties-reference.md)