---
title: "Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt; | Microsoft Docs"
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
  - "vs.tasklisterror.licx_generator_failed"
ms.assetid: 875e948c-d7a3-4ffc-be0d-f341de5f6310
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not transform licenses file &#39;file&#39; into a binary resource. &lt;reason&gt;
Die Verarbeitung durch den Lizenzprozessor, der zur Umwandlung von LICX\-Dateien in binäre Ressourcen verwendet wird, ist fehlgeschlagen.  
  
 Dieser Fehler wird normalerweise durch eine fehlerhafte LICX\-Datei verursacht.  Möglicherweise ist die Datei in einem Texteditor geöffnet und geändert worden.  
  
 Der Buildprozess schlägt fehl, wenn dieser Fehler auftritt.  
  
### So beheben Sie diesen Fehler  
  
1.  Wählen Sie das Projekt im Projektmappen\-Explorer aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Alle Dateien anzeigen**.  
  
3.  Erweitern Sie im Projektmappen\-Explorer den Ordner obj, und erweitern Sie dann den Ordner **Debug**.  
  
4.  Suchen Sie die Datei mit dem Namen "myApplication.exe.licenses". Dabei entspricht myApplication dem Namen der Windows Forms\-Anwendung.  
  
5.  Löschen Sie diese Datei, und erstellen Sie die Projektmappe neu.  
  
## Siehe auch  
 [How to: License Components and Controls](../Topic/How%20to:%20License%20Components%20and%20Controls.md)