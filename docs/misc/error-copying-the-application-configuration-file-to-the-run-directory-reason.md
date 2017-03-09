---
title: "Error copying the application configuration file to the run directory. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.cant_copy_appcfg_file"
ms.assetid: 15699a76-16ef-40a8-8ed4-5eef4d2c0e72
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error copying the application configuration file to the run directory. &lt;reason&gt;
Das Projektsystem kann die **app.config**\-Datei nicht in das Verzeichnis kopieren, von dem aus das Projekt ausgeführt wird.  Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
 Dieser Fehler tritt nur beim Erstellen einer EXE\-Datei auf.  
  
 Das Buildsystem sucht eine Datei mit der Bezeichnung **app.config** im Stammordner des Projekts.  Diese Datei wird in das Ausgabeverzeichnis des Projekts kopiert. Der Name im Ausgabeverzeichnis lautet *outputfile.*.config.  
  
 Für diese Fehlermeldung kommen folgende Ursachen in Frage:  
  
-   Kein Speicherplatz vorhanden  
  
-   MAX\_PATH überschritten  
  
 Vergewissern Sie sich, dass keine andere Kopie der laufenden Anwendung vorhanden ist.  
  
## Siehe auch  
 [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/de-de/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)