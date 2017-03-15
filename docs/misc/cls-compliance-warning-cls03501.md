---
title: "CLS-Kompatibilit&#228;t: Warnung CLS03501 | Microsoft Docs"
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
  - "CLS03501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03501"
ms.assetid: 26a08830-9c8a-4bf6-931d-e0c523f1eb21
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS03501
Nach der CLS sind öffentlich sichtbare erforderliche Modifizierer \(modreq\) nicht zulässig, allerdings sind optionale Modifizierer \(modopt\), die sie nicht versteht, zulässig.  
  
 Nach der CLS sind öffentlich sichtbare erforderliche Modifizierer \(modreq\) nicht zulässig, allerdings sind optionale Modifizierer \(modopt\), die sie nicht versteht, zulässig.  
  
 Stellen Sie sicher, dass Konstruktorsignaturen keine Typen enthalten, die mit öffentlich sichtbaren, erforderlichen Modifizierern gekennzeichnet.  
  
 Weitere Informationen zur Überprüfung der CLS\-Kompatibilität \(Common Language Subset\) finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS03501 generiert:  
  
```  
// CLS03501.cpp // compile with: /clr /LD // CLS03501 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: One(volatile Int32 param) {}   // CLS03501 One( Int32 param1, Int32 param2) {}   // OK };  
```