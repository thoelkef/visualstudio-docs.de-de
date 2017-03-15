---
title: "CLS-Kompatibilit&#228;tswarnung CLS03503 | Microsoft Docs"
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
  - "CLS03503"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03503"
ms.assetid: 2d2e78db-5fcf-47e1-af1e-9545f28a306b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS03503
Nach der CLS sind öffentlich sichtbare erforderliche Modifizierer \(modreq\) nicht zulässig, allerdings sind optionale Modifizierer \(modopt\), die sie nicht versteht, zulässig.  
  
 Nach der CLS sind öffentlich sichtbare erforderliche Modifizierer \(modreq\) nicht zulässig, allerdings sind optionale Modifizierer \(modopt\), die sie nicht versteht, zulässig.  
  
 Stellen Sie sicher, dass Felder keine Typen enthalten, die mit öffentlich sichtbaren, erforderlichen Modifizierern gekennzeichnet sind.  
  
 Weitere Informationen zur Überprüfung der CLS\-Kompatibilität \(Common Language Subset\) finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS03503 generiert:  
  
```  
// CLS03503.cpp // compile with: /clr /LD // CLS03503 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class MyClass { public: volatile Int32 param;   // CLS03503 Int32 param2;   // OK };  
```