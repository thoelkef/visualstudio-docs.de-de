---
title: "MSBuild Error MSB3128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.ManifestsSignedHashExcluded"
helpviewer_keywords: 
  - "MSB3128"
ms.assetid: e8612a4b-4016-48d2-b5f0-a1091bfe8cb1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3128
**MSB3128: Die ClickOnce\-Manifeste können nicht signiert werden, weil sie mindestens einen Verweis ohne Hash enthalten.**  
  
 Wenn Sie eine Anwendung veröffentlichen, die über ein signiertes Manifest verfügt, müssen alle Dateien im Hash eingeschlossen sein.  
  
### So beheben Sie diesen Fehler  
  
1.  Wechseln Sie im **Projekt\-Designer** zur Seite **Veröffentlichen**.  
  
2.  Klicken Sie auf **Anwendungsdateien**.  
  
3.  Legen Sie den Wert von **Hash** für alle zu veröffentlichenden Dateien auf **Einschließen** fest.  
  
## Siehe auch  
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)