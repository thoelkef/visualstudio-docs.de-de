---
title: "Problembehandlung bei Ausnahmen: System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "InvalidCastException-Klasse"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.InvalidCastException
Eine <xref:System.InvalidCastException>\-Ausnahme wird ausgelöst, wenn ein Fehler während einer expliziten Verweiskonvertierung auftritt. Verweiskonvertierungen sind Konvertierungen von einem Referenztyp zu einem anderen. Dabei kann der Typ des Verweises geändert werden, nie jedoch der Typ oder Wert des Konvertierungsziels. Typumwandlung bei Objekten ist ein häufiger Grund für diese Ausnahme.  
  
## Tipps  
 **Vergleichen Sie die Quelltypen mit den Zieltypen, um sicherzustellen, dass die Konvertierung gültig ist.**  
 Informationen über Konvertierungen, die vom System unterstützt werden, finden Sie unter <xref:System.Convert>.  
  
## Hinweise  
 Damit eine explizite Verweiskonvertierung erfolgreich ist, muss der Quellwert NULL sein \(`Nothing` in Visual Basic\), oder der Objekttyp, auf den das Quellargument verweist, muss durch implizite Verweiskonvertierung in den Zieltyp konvertierbar sein.  
  
 Wenn eine Visual Basic 6.0\-Anwendung mit einem Aufruf eines benutzerdefinierten Ereignisses in einem Benutzersteuerelement auf eine neue Version von Visual Basic aktualisiert und dann ausgeführt wird, wird diese Ausnahme womöglich durch folgende Information ergänzt: "Die angegebene Umwandlung ist ungültig." Um diesen Fehler zu beheben, suchen Sie die folgende Codezeile in  `Form1`:  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 Und ersetzen Sie sie durch:  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## Siehe auch  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [Konvertieren von Zeichenfolgen in .NET Framework\-Datentypen](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [Gewusst wie: Implementieren von benutzerdefinierten Konvertierungen zwischen Strukturen](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)