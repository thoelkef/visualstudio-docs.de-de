---
title: "Problembehandlung bei Ausnahmen: System.OperationCanceledException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OperationCanceledException-Klasse"
ms.assetid: 275e2887-7491-432b-9b80-a21bb794be29
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.OperationCanceledException
<xref:System.OperationCanceledException> wird ausgelöst, wenn bei einer Operation <xref:Microsoft.VisualBasic.FileIO.UICancelOption> auf `ThrowException` festgelegt wurde und die Operation abgebrochen wird.  
  
## Tipps  
 Wenn Sie nicht möchten, dass diese Ausnahme ausgelöst wird, legen Sie <xref:System.OperationCanceledException> auf `DoNothing` fest.  
 Der Standardwert von <xref:Microsoft.VisualBasic.FileIO.UICancelOption> ist `ThrowException`. Wenn Sie nicht möchten, dass die Ausnahme beim Abbruch einer Operation durch den Benutzer ausgelöst wird, legen Sie den Enumerationswert auf `DoNothing` fest.  
  
## Siehe auch  
 <xref:System.OperationCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)