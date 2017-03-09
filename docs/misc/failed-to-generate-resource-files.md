---
title: "Failed to generate resource files | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resource_prep_failed"
ms.assetid: 81ffe283-0782-4559-8dcd-edfec7d6fc8b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Failed to generate resource files
Ein allgemeiner Fehler trat auf, als das Projektsystem beim Erstellen von binären Ressourcendateien eine RESX\-Datei lesen wollte, die der .NET Ressourcen\-Manager einlesen kann.  
  
 Dieser Fehler wird normalerweise durch eine fehlerhafte RESX\-Datei verursacht.  
  
 Durch diesen Fehler schlägt das Build nicht fehl.  Allerdings wird die RESX\-Datei, für die dieser Fehler angezeigt wird, nicht als Assemblymanifestressource in das Projekt eingefügt.  
  
## Siehe auch  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/de-de/f793852c-da06-4d52-a826-65f635844772)