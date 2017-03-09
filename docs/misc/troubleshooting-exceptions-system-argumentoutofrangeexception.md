---
title: "Problembehandlung bei Ausnahmen: System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
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
  - "ArgumentOutOfRangeException-Klasse"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ArgumentOutOfRangeException
Eine <xref:System.ArgumentOutOfRangeException>\-Ausnahme wird ausgelöst, wenn eine Methode aufgerufen wird und mindestens eines der an die Methode übergebenen Argumente kein Nullverweis ist \(`Nothing` in Visual Basic\) und keinen gültigen Wert enthält.  
  
## Tipps  
 **Stellen Sie sicher, dass alle Argumente dieser Methode über gültige Werte verfügen, wie von der aufgerufenen Methode definiert.**  
 Argumente, die keine Nullverweise sind, müssen gültige Werte enthalten.  
  
 **Vergewissern Sie sich beim Arbeiten mit einer Auflistung, dass der Index kleiner als die Größe der Auflistung ist.**  
 Der Index muss innerhalb des Größenbereichs der Auflistung liegen. Er darf den Größenbereich nicht überschreiten und auch nicht kleiner als 0 sein. Weitere Informationen finden Sie unter [Auflistungen](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
 **Überprüfen Sie den startIndex\-Parameter, wenn Sie die überladenen, zwei Argumente benötigenden FindString\-Methoden oder FindExactString\-Methoden der Kombinationsfeld\-Klasse oder der ListBox\-Klasse verwenden**.  
 Dies Ausnahme wird möglicherweise ausgelöst, wenn `startIndex` gleich dem Indexwert des letzten Elements in der zugeordneten Liste ist. Übergeben Sie 0 als `startIndex`\-Parameter, oder verwenden Sie die `FindString`\-Methode oder die `FindStringExact`\-Methode mit nur einem Argument, um diesen Fehler zu umgehen. Weitere Informationen finden Sie unter [CComboBox::FindString](../Topic/CComboBox::FindString.md) oder [CListBox::FindString](../Topic/CListBox::FindString.md).  
  
## Siehe auch  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)