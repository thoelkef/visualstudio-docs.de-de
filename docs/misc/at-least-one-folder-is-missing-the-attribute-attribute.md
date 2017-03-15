---
title: "At least one folder is missing the &#39;attribute&#39; attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_missing_fold_attrib"
ms.assetid: 3a0498a9-df61-47d8-a228-f88f4f138df8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one folder is missing the &#39;attribute&#39; attribute
In einem Ordnerknoten, der aus der VBPROJ\-Datei oder der CSPROJ\-Datei gelesen wurde, fehlen bestimmte Attribute, die für das Projektsystem erforderlich sind.  Zurzeit ist das **RelPath**\-Attribut das einzige Attribut, das angibt, wo sich der Ordner unter dem Projektordner befindet.  
  
 Dieser Fehler wird meistens durch das manuelle Bearbeiten der Projektdatei verursacht.  
  
 **So beheben Sie diesen Fehler**  
  
-   Entfernen Sie den betreffenden Ordnerknoten aus der Projektdatei.  Wenn sich der Ordner noch auf der Festplatte befindet, können Sie in den Modus Alle Dateien anzeigen wechseln \(indem Sie auf die entsprechende Schaltfläche auf der Symbolleiste des Projektmappen\-Explorers klicken\), mit der rechten Maustaste auf den betroffenen Ordner klicken und **Zu Projekt hinzufügen** wählen.  
  
     Ordner, denen ein Attribut fehlt, werden dem Projekt nicht hinzugefügt.  
  
## Siehe auch  
 [Projektdateien](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)