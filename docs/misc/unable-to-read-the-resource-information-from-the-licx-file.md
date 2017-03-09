---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
Die LICX\-Datei konnte vom Projekt nicht gelesen werden.  Als Teil der Lizenzvorbereitung wandelt das Projektsystem LICX\-Textdateien in binäre Ressourcendateien um, die für das COM\+\-Lizenzierungsmodell geeignet sind.  
  
 Die LICX\-Datei wird vom Windows Forms\-Designer automatisch generiert oder aktualisiert, sobald dem Formular ein lizenziertes Steuerelement hinzugefügt wird.  Es gibt eine LICX\-Datei pro Projekt. Sie befindet sich immer im Stammverzeichnis und erhält immer den Namen **licenses.licx**.  
  
 Für diese Fehlermeldungen kommen folgende Ursachen in Frage:  
  
-   Zugriff verweigert.  
  
-   Verbindung zum Webserver für Webprojekte unterbrochen.  
  
 Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
## Siehe auch  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)