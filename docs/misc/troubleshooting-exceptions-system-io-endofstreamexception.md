---
title: "Problembehandlung bei Ausnahmen: System.IO.EndOfStreamException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "EndOfStreamException-Klasse"
ms.assetid: 1271e6f6-3a0d-49f0-9ff4-178d480687be
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IO.EndOfStreamException
Eine <xref:System.IO.EndOfStreamException>\-Ausnahme wird bei dem Versuch ausgelöst, über das Ende eines Streams hinaus zu lesen.  
  
## Tipps  
 **Überprüfen Sie vor dem Lesen, ob das Ende der Datei erreicht ist.**  
 Verwenden Sie die <xref:System.IO.StreamReader.Peek%2A>\-Methode, um vor dem Lesen des Streams das Dateiende zu überprüfen.  
  
## Siehe auch  
 <xref:System.IO.EndOfStreamException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Gewusst wie: Lesen und Schreiben einer neu erstellten Datendatei](../Topic/How%20to:%20Read%20and%20Write%20to%20a%20Newly%20Created%20Data%20File.md)   
 [Gewusst wie: Öffnen und Anfügen an eine Protokolldatei](../Topic/How%20to:%20Open%20and%20Append%20to%20a%20Log%20File.md)