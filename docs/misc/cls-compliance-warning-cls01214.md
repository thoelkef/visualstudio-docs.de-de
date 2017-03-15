---
title: "CLS-Kompatibilit&#228;tswarnung CLS01214 | Microsoft Docs"
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
  - "CLS01214"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01214"
ms.assetid: 5968af20-3d3e-4c7b-ad61-c06979cc9efd
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01214
Die Sichtbarkeit und der Zugriff von Typen und Membern soll so beschaffen sein, dass Typen in der Signatur eines Members sichtbar und zugreifbar sind, wann immer der Member selbst sichtbar und zugreifbar ist. Zum Beispiel soll ein Delegat, der außerhalb der Assembly sichtbar ist, nicht über ein Argument verfügen, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Typen in Delegatsignaturen müssen eine größere oder gleiche Zugreifbarkeit wie der Delegat aufweisen.  Zum Beispiel soll ein Delegat, der außerhalb der Assembly sichtbar ist, nicht über ein Argument verfügen, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS01214 generiert:  
  
```  
/* CLS01214.cpp */ // compile with: /clr /LD // CLS01214 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicType {}; private ref class AssemblyType {}; public delegate PublicType^ AssemblyDelegate(AssemblyType^ parameter);   // not cls compliant public delegate PublicType^ AssemblyDelegate2(PublicType^ parameter);   //cls compliant  
```