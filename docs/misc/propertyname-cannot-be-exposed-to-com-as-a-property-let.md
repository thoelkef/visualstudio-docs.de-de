---
title: "&#39;&lt;Eigenschaftenname&gt;&#39; kann nicht als „Let“-Eigenschaft f&#252;r COM verf&#252;gbar gemacht werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42102"
  - "vbc42102"
helpviewer_keywords: 
  - "BC42102"
ms.assetid: b77c5b7c-ac43-4b2d-b8bc-582e65e6f7e7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Eigenschaftenname&gt;&#39; kann nicht als „Let“-Eigenschaft f&#252;r COM verf&#252;gbar gemacht werden.
'\<Eigenschaftenname\>' kann nicht als „Let“\-Eigenschaft für COM verfügbar gemacht werden. Sie können dieser Eigenschaft mit der Let\-Anweisung keine Werte \(z. B. Zahlen oder Zeichenfolgen\) aus Visual Basic 6.0 zuweisen, die keine Objekte sind.  
  
 Eine Klasse mit einem `COMClassAttribute`\-Attributblock deklariert eine `Public`\-Eigenschaft mit dem Datentyp `Object`. Ein Visual Basic 6.0\-Programm kann auf diese Eigenschaft als `Variant` zugreifen. Es kann mit der `Set`\-Anweisung jedoch nur einen Objektverweis darauf zuweisen. Es kann mit der `Let`\-Anweisung keinen Werttyp zuweisen.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42102  
  
### So reagieren Sie auf diese Warnung  
  
-   Ziehen Sie in Betracht, potenzielle Visual Basic 6.0\-Benutzer über diese Klasse zu informieren, da sie diese Eigenschaft nicht mit der `Let`\-Anweisung verwenden können.  
  
## Siehe auch  
 [Default Property Changes in Visual Basic](http://msdn.microsoft.com/de-de/9b8cfad7-40ac-4b83-affb-1ff781755a4c)   
 [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Public](/dotnet/visual-basic/language-reference/modifiers/public)   
 [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type)   
 [NICHT IM BUILD: In Visual Basic verwendete Attribute](http://msdn.microsoft.com/de-de/22231318-8a40-49af-9245-e0aab723563b)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute\-Klasse](http://msdn.microsoft.com/de-de/5c2f0835-9210-47dc-bc59-5c1769953574)