---
title: "At least one file is missing the &#39;attribute&#39; attribute | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_missing_file_attrib"
ms.assetid: 2627974b-c9cd-4d85-9af4-dd3811214ea4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one file is missing the &#39;attribute&#39; attribute
In einem Dateiknoten, der aus der VBPROJ\-Datei oder der CSPROJ\-Datei gelesen wurde, fehlen bestimmte Attribute, die für das Projektsystem erforderlich sind.  Zurzeit ist das `RelPath`\-Attribut das einzige Attribut, das angibt, wo sich die Datei unter dem Projektordner befindet.  
  
 Dieser Fehler wird meistens durch das manuelle Bearbeiten der Projektdatei verursacht.  
  
 **So beheben Sie diesen Fehler**  
  
-   Entfernen Sie den betreffenden Dateiknoten aus der Projektdatei.  Wenn sich die Datei noch auf dem Datenträger befindet, können Sie in den Modus **Alle Dateien anzeigen** wechseln \(indem Sie auf die entsprechende Schaltfläche auf der Symbolleiste des Projektmappen\-Explorers klicken\), mit der rechten Maustaste auf die betroffene Datei klicken und **Zu Projekt hinzufügen** wählen.  
  
     Dateien, denen das `RelPath`\-Attribut fehlt, werden dem Projekt nicht hinzugefügt.  
  
## Siehe auch  
 [Projektdateien](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)