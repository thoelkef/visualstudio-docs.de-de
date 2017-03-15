---
title: "Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39; | Microsoft Docs"
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
  - "vs.tasklisterror.resource_naming_conflict"
ms.assetid: 50d656ad-8557-4240-95b0-3f44b9c21da6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resources &#39;file1&#39; and &#39;file2&#39; have the same manifest resource name &#39;name&#39;
Das Projektsystem hat identische Assemblyressourcennamen für zwei Dateien ermittelt, deren `BuildAction`\-Eigenschaft auf `EmbeddedResource` festgelegt ist und die über eine neutrale Kultur verfügen.  Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  Weitere Informationen zur `BuildAction`\-Eigenschaft finden Sie unter [File Properties](http://msdn.microsoft.com/de-de/013c4aed-08d6-4dce-a124-ca807ca08959).  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] verfügt über kein ordnerbasiertes Namespacekonzept. Ressourcendateien mit den Namen:  
  
-   Proj1\\OrdnerA\\MeinProj.bmp  
  
-   Proj1\\OrdnerB\\MeinProj.bmp  
  
 erstellen daher Assemblymanifestnamen nach dem Muster **Proj1.MeinProj.bmp** für beide Dateien.  
  
 **So beheben Sie diesen Fehler**  
  
-   Benennen Sie zum Beheben dieses Fehlers die betreffenden Ressourcendateien \(*Datei1* und *Datei2*\) um.  
  
## Siehe auch  
 [NIB: Resource File Naming Conventions](http://msdn.microsoft.com/de-de/7b1a2cdf-6196-4034-8fc7-51a271842cc2)