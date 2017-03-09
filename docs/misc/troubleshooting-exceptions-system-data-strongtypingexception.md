---
title: "Problembehandlung bei Ausnahmen: System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StrongTypingException-Klasse"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Data.StrongTypingException
Eine <xref:System.Data.StrongTypingException> tritt auf, wenn der Benutzer auf einen <xref:System.DBNull>\-Wert in einem stark typisierten <xref:System.Data.DataTable.DataSet%2A> zugreift.  
  
## Tipps  
 **Fügen Sie eine Fehlerbehandlung für die StrongTypingException hinzu.**  
 Platzieren Sie den Code, der auf das <xref:System.Data.DataTable.DataSet%2A> zugreift, in einem `Try…Catch`\-Block, und fangen Sie die <xref:System.Data.StrongTypingException> ab.  
  
## Siehe auch  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Arbeiten mit Datasets in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)