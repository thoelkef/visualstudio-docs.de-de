---
title: "Problembehandlung bei Ausnahmen: System.Net.CookieException | Microsoft Docs"
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
  - "CookieException-Klasse"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Net.CookieException
Eine <xref:System.Net.CookieException>\-Ausnahme wird ausgelöst, wenn ein Fehler beim Hinzufügen eines Cookies in einen Cookiecontainer auftritt.  
  
## Tipps  
 **Stellen Sie sicher, dass die Cookiegröße nicht die vom Cookiecontainer zugelassene Größe überschreitet.**  
 Die Ausnahme wird bei dem Versuch ausgelöst, ein <xref:System.Net.Cookie>, das länger als <xref:System.Net.CookieContainer.MaxCookieSize%2A> ist, zu <xref:System.Net.CookieContainer> hinzuzufügen. Die standardmäßige maximale Cookiegröße ist 4096 Bytes.  
  
 **Wenn Sie die Name\-Eigenschaft für ein Cookie festlegen, stellen Sie sicher, dass der Wert weder ein NULL\-Verweis noch eine leere Zeichenfolge ist.**  
 Die <xref:System.Net.Cookie.Name%2A>\-Eigenschaft muss vor dem Verwenden einer Instanz der <xref:System.Net.Cookie>\-Klasse initialisiert werden. Die folgenden Zeichen sind reserviert und können nicht für den Wert dieses Attributs verwendet werden: Gleichheitszeichen, Semikolon, Komma, neue Zeile \(\\n\), Wagenrücklaufzeichen \(\\r\), Tabstoppzeichen \(\\t\). Das Dollarzeichen \($\) darf nicht das erste Zeichen sein.  
  
 **Wenn Sie die Port\-Eigenschaft für ein Cookie festlegen, stellen Sie sicher, dass der Wert gültig und in doppelte Anführungszeichen eingeschlossen ist.**  
 Das <xref:System.Net.Cookie.Port%2A>\-Attribut schränkt die Anschlüsse ein, an die ein Cookie gesendet werden kann. Der Standardwert bedeutet keinerlei Beschränkung. Durch das Festlegen der Eigenschaft auf eine leere Zeichenfolge \(""\) wird der Anschluss auf den einen Anschluss beschränkt, der in der HTTP\-Antwort verwendet wird. Andernfalls muss der Wert eine in Anführungszeichen gesetzte Zeichenfolge sein, in der die Anschlusswerte mit Kommas abgegrenzt sind.  
  
 **Wenn Sie die Value\-Eigenschaft für ein Cookie festlegen, stellen Sie sicher, dass der Wert nicht NULL ist.**  
 Die folgenden Zeichen sind reserviert und können nicht für diese Eigenschaft verwendet werden: Semikolon, Komma.  
  
## Siehe auch  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)