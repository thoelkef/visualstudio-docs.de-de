---
title: "Problembehandlung bei Ausnahmen: System.ArgumentNullException | Microsoft Docs"
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
  - "ArgumentNullException-Klasse"
ms.assetid: 5f21413c-d997-47c6-9b06-3d85a719d51b
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ArgumentNullException
Eine <xref:System.ArgumentNullException>\-Ausnahme wird ausgelöst, wenn ein NULL\-Verweis \(`Nothing` in Visual Basic\) an eine Methode übergeben wird, die diesen nicht als gültiges Argument akzeptiert.  
  
## Tipps  
 **Überprüfen Sie die Argumente, um sicherzustellen, dass sie nicht NULL sind \(Nothing in Visual Basic\).**  
 Ein NULL\-Verweis ist ein Verweis auf ein Objekt, das nicht existiert. Dies kommt oft vor, wenn keine Instanz des Objekts programmgesteuert erstellt wurde.  
  
## Hinweise  
 <xref:System.ArgumentNullException> verhält sich genauso wie <xref:System.ArgumentException>. Diese Ausnahme wird angegeben, damit der Anwendungscode zwischen den Ausnahmen unterscheiden kann, die durch ein NULL\-Argument und die durch ein Nicht\-NULL\-Argument verursacht wurden. Fehler, die von Nicht\-NULL\-Argumenten verursacht wurden, finden Sie unter [Problembehandlung bei Ausnahmen: System.ArgumentOutOfRangeException](../misc/troubleshooting-exceptions-system-argumentoutofrangeexception.md).  
  
## Siehe auch  
 <xref:System.ArgumentNullException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)