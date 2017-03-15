---
title: "„Global“ ist in diesem Kontext nicht zul&#228;ssig. Es wird ein Bezeichner erwartet. | Microsoft Docs"
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
  - "vbc36001"
  - "bc36001"
helpviewer_keywords: 
  - "BC36001"
ms.assetid: d515daa2-f53d-424c-81fd-e9c4b12f331b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Global“ ist in diesem Kontext nicht zul&#228;ssig. Es wird ein Bezeichner erwartet.
Das `Global`\-Schlüsselwort wird in einer Anweisung verwendet, in der es nicht zulässig ist.  
  
 Das `Global`\-Schlüsselwort ermöglicht Ihnen den Zugriff auf einen Namespace, der außerhalb der Namespacehierarchie definiert ist, in der der Code kompiliert werden soll.`Global` startet den Qualifizierungspfad auf der äußersten Namespaceebene der .NET Framework\-Klassenbibliothek. Eine Veranschaulichung finden Sie unter [Global – Löschen](http://msdn.microsoft.com/de-de/18c8ba14-40f6-4978-8096-6a5852324635).  
  
 Bestimmte Anweisungen, wie z. B. `Imports` und `Namespace`, sind unabhängig vom Namespace, in dem der Code kompiliert werden soll. Es ist ein vollständiger Qualifizierungspfad erforderlich, beginnend mit dem Namespace auf Stammebene, z. B. <xref:System> oder <xref:Microsoft.VisualBasic>. In solchen Aussagen ist das `Global`\-Schlüsselwort überflüssig und nicht erlaubt.  
  
 **Fehler\-ID:** BC36001  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Global`\-Schlüsselwort aus der Anweisung. Es ist nicht erforderlich.  
  
## Siehe auch  
 [Global – Löschen](http://msdn.microsoft.com/de-de/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)