---
title: "Compilerfehler CS1569 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1569"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1569"
ms.assetid: 1d5e89d6-0a05-4e4f-b472-9089146696bb
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1569
Fehler beim Generieren der XML\-Dokumentationsdatei 'dateiname' \('ursache'\)  
  
 Beim Versuch, die XML\-Dokumentation in die in der Meldung genannte Datei zu schreiben, ist aus dem angegebenen Grund ein Fehler aufgetreten. Die Ursache kann etwas in der Art von „Netzlaufwerk nicht gefunden“ oder „Zugriff verweigert“ sein. Häufig lassen sich aus der Ursache bereits Maßnahmen zum Beheben des Fehlers ableiten. Wenn beispielsweise der Fehler "Zugriff verweigert" angezeigt wird, liegt es nahe, die Schreibberechtigungen für die Datei zu überprüfen.  
  
## Beispiel  
  
```  
// 1569a.cs // compile with: /doc:CS1569.xml // post-build command: attrib +r CS1569.xml class Test { /// <summary>Test.</summary> public static void Main() {} }  
```  
  
## Beispiel  
 Im vorhergehenden Beispiel wurde eine XML\-Datei generiert, die dann auf schreibgeschützt festgelegt wurde. In diesem Beispiel wird versucht, in die gleiche Datei zu schreiben. Im folgenden Beispiel wird CS1569 generiert:  
  
```  
// CS1569.cs // compile with: /doc:CS1569.xml // CS1569 expected class Test { /// <summary>Test.</summary> public static void Main() {} }  
  
```