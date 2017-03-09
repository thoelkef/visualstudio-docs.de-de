---
title: "CLS-Kompatibilit&#228;tswarnung CLS01203 | Microsoft Docs"
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
  - "CLS01203"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01203"
ms.assetid: fe27463a-27df-473b-985a-b04c3bfac4d3
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01203
Die Sichtbarkeit und der Zugriff von Typen und Membern soll so beschaffen sein, dass Typen in der Signatur eines Members sichtbar und zugreifbar sind, wann immer der Member selbst sichtbar und zugreifbar ist. Zum Beispiel soll ein öffentliches Feld, das außerhalb der Assembly sichtbar ist, keinen Typen aufweisen, der nur innerhalb der Assembly sichtbar ist.  
  
 Die Sichtbarkeit und der Zugriff von Typen und Membern soll so beschaffen sein, dass Typen in der Signatur eines Members sichtbar und zugreifbar sind, wann immer der Member selbst sichtbar und zugreifbar ist. Zum Beispiel soll ein öffentliches Feld, das außerhalb der Assembly sichtbar ist, keinen Typen aufweisen, der nur innerhalb der Assembly sichtbar ist.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS01203 generiert:  
  
```  
/* CLS01203.cpp */ // compile with: /clr /LD // CLS01203 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Member1;   // not cls compliant PublicLevelType^ Member2;   // cls compliant };  
```