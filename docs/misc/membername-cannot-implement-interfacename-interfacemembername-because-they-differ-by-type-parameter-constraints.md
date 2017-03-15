---
title: "&#39;&lt;Membername&gt;&#39; kann &#39;&lt;Schnittstellenname&gt;.&lt;Schnittstellenmembername&gt;&#39; nicht implementieren, da sie unterschiedliche Typparametereinschr&#228;nkungen aufweisen. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32078"
  - "BC32078"
helpviewer_keywords: 
  - "BC32078"
ms.assetid: 2c971345-edb4-491e-9202-8eb8286b66f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Membername&gt;&#39; kann &#39;&lt;Schnittstellenname&gt;.&lt;Schnittstellenmembername&gt;&#39; nicht implementieren, da sie unterschiedliche Typparametereinschr&#228;nkungen aufweisen.
Ein allgemeines Ereignis, eine Eigenschaft oder eine Prozedur versucht, einen ähnlichen in einer Schnittstelle definierten Member zu implementieren, aber sie verfügen über unterschiedliche Einschränkungslisten für ihre Typparameter.  
  
 Um ein Schnittstellenmember zu implementieren, muss der implementierende Member nicht nur mit der vollständigen Signatur des Schnittstellenmembers übereinstimmen, sondern auch mit dem Übergabemechanismus für die einzelnen Parameter.  
  
 Der implementierende Member muss zusätzlich hinsichtlich der Anzahl der Typparameter und der Einschränkungsliste der einzelnen Parameter übereinstimmen, um einen allgemeinen Schnittstellenmember zu implementieren.  
  
 Einzelheiten zur Schnittstellenimplementierung finden Sie unter [NICHT IM BUILD: Implements\-Schlüsselwort und Implements\-Anweisung](http://msdn.microsoft.com/de-de/b96560f7-6413-480f-a1e2-f80253bab5be).  
  
 **Fehler\-ID:** BC32078  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie beabsichtigen, den Schnittstellenmember zu implementieren, überarbeiten Sie die Typparametereinschränkungen, damit diese genau mit denen des Schnittstellenmembers übereinstimmen.  
  
-   Wenn die Typparametereinschränkungen unverändert bleiben müssen, können Sie den Schnittstellenmember in dieser Deklaration nicht implementieren. Entfernen Sie das [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)\-Schlüsselwort aus der Deklaration.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NICHT IM BUILD: Beispiele für die Schnittstellenimplementierung in Visual Basic](http://msdn.microsoft.com/de-de/50bf2a30-73b6-4126-a921-075fd6eec278)