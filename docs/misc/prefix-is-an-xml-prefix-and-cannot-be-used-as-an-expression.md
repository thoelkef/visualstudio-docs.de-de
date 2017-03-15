---
title: "&#39;prefix&#39; ist ein XML-Pr&#228;fix und kann nicht als Ausdruck verwendet werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30114"
  - "vbc30114"
helpviewer_keywords: 
  - "BC30114"
ms.assetid: 5cb7c89e-c61b-483a-9369-5285b7cbcf45
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;prefix&#39; ist ein XML-Pr&#228;fix und kann nicht als Ausdruck verwendet werden
'prefix' ist ein XML\-Präfix und kann nicht als Ausdruck verwendet werden. Verwenden Sie die GetXmlNamespace\-Operator, um ein Namespaceobjekt zu erstellen.  
  
 Das Präfix für einen XML\-Namespace, der mithilfe der `Imports`\-Anweisung importiert wird, kann nicht außerhalb eines XML\-Literals verwendet werden.  
  
 **Fehler\-ID:** BC30114  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie auf einen Teil des importierten XML\-Namespaces verweisen müssen, verwenden Sie den `GetXmlNamespace`\-Operator, um ein <xref:System.Xml.Linq.XNamespace>\-Objekt abzurufen. Verwenden Sie dieses Objekt anstelle des XML\-Namespacepräfixes.  
  
-   Wenn Sie das XML\-Namespacepräfix verwenden, um ein XML\-Literal zu qualifizieren, stellen Sie sicher, dass Sie die entsprechende Syntax für das XML\-Literal verwenden.  
  
## Siehe auch  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [GetXmlNamespace Operator](/dotnet/visual-basic/language-reference/operators/getxmlnamespace-operator)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)