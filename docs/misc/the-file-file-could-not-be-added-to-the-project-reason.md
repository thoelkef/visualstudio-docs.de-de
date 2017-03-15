---
title: "Die Datei „datei“ konnte dem Projekt nicht hinzugef&#252;gt werden. &lt;Ursache&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.projfile_no_add_file"
ms.assetid: 8bd70556-596a-4e24-a71c-a340604ee93d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Datei „datei“ konnte dem Projekt nicht hinzugef&#252;gt werden. &lt;Ursache&gt;
Eine Datei, die aus der VBPROJ\- oder CSPROJ\-Datei gelesen wurde, kann dem Projekt nicht hinzugefügt werden. Dies kann u.a. folgende Gründe haben:  
  
-   Ungültiger Dateiname.  
  
-   Datei innerhalb eines Pfads. Nehmen Sie an, Sie haben einen projektbezogenen Pfad „Datei1\\Datei2.txt“, es gibt jedoch auch ein Ordner mit dem relativen Pfad „Datei1\\Datei2.txt“.  
  
-   Das Element ist bereits vorhanden. Dieser Fall tritt ein, wenn eine Datei zwei Mal in der Projektdatei aufgelistet ist.  
  
-   Der Link ist bereits vorhanden. Das Projektsystem von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] und [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] weist insofern eine Einschränkung auf, als dass immer nur ein Link mit gleichem Namen pro Projekt vorkommen kann. Dies bedeutet beispielsweise, dass Sie nicht in Ordner A und Ordner B des Projekts einen Link auf „file.vb“ verwenden können.  
  
 Dieser Fehler wird wahrscheinlich durch das manuelle Bearbeiten der Projektdatei hervorgerufen.  
  
 Dateien, für die dieses Diagnoseergebnis angezeigt wird, werden dem Projekt nicht hinzugefügt.  
  
## Siehe auch  
 [Projektdateien](/visual-cpp/ide/project-files)   
 [NIB: Elementverwaltung in Projekten](http://msdn.microsoft.com/de-de/762e606b-7f44-4b66-97a1-e30a703654a0)