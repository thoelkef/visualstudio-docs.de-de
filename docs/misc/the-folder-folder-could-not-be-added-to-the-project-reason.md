---
title: "The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_folder"
ms.assetid: 3f6a5aa7-17cc-4e78-93b7-96e0970e111e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The folder &#39;folder&#39; could not be added to the project. &lt;reason&gt;
Ein Ordner, der aus der VBPROJ\-Datei oder der CSPROJ\-Datei gelesen wird, kann dem Projekt nicht hinzugefügt werden.  Folgende Gründe können vorliegen:  
  
-   Ungültiger Name  
  
-   Datei innerhalb eines Pfads.  Sie haben z. B. einen projektbezogenen Pfad von **Ordner1\\Ordner2\\Ordner3**, es gibt jedoch auch eine Datei mit dem relativen Pfad **Ordner1\\Ordner2**.  
  
-   Element ist bereits vorhanden.  Dies tritt auf, wenn ein Ordner zwei Mal in der Projektdatei aufgelistet ist.  
  
 Dieser Fehler wird meistens durch das manuelle Bearbeiten der Projektdatei verursacht.  
  
 **So beheben Sie diesen Fehler**  
  
-   Entfernen Sie den betreffenden Ordnerknoten aus der Projektdatei.  
  
     Ordner und Dateien unterhalb der Ordnerhierarchie, für die die Diagnose angezeigt wird, werden dem Projekt nicht hinzugefügt.  
  
## Siehe auch  
 [Projektdateien](/visual-cpp/ide/project-files)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/de-de/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)