---
title: "Problembehandlung bei Ausnahmen: System.Drawing.Printing.InvalidPrinterException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InvalidPrinterException-Klasse"
ms.assetid: e19b9b9c-2b0f-4839-85c0-ae75e1c356d2
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Drawing.Printing.InvalidPrinterException
Eine <xref:System.Drawing.Printing.InvalidPrinterException>\-Ausnahme wird ausgelöst, wenn versucht wird, einen Drucker mit ungültigen Druckereinstellungen zu verwenden.  
  
## Tipps  
 **Stellen Sie sicher, dass der Drucker vorhanden ist.**  
 Die häufigste Ursache für ungültige Druckereinstellungen besteht im Verweis auf einen nicht vorhandenen Drucker. Weitere Informationen finden Sie unter <xref:System.Drawing.Printing>.  
  
 **Stellen Sie sicher, dass ein Standarddrucker installiert worden ist.**  
 Wenn kein Drucker angegeben wurde, vergewissern Sie sich, ob ein Standarddrucker installiert worden ist. Weitere Informationen finden Sie unter <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>  
  
## Siehe auch  
 <xref:System.Drawing.Printing.InvalidPrinterException>   
 <xref:System.Drawing.Printing.PrinterSettings>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)