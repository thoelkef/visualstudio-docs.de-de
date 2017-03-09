---
title: "CLS-Kompatibilit&#228;tswarnung CLS01202 | Microsoft Docs"
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
  - "CLS01202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01202"
ms.assetid: ab75e9c4-9d87-4bb4-ad8f-3e6ab5559de7
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01202
Die Sichtbarkeit und der Zugriff von Typen und Membern soll so beschaffen sein, dass Typen in der Signatur eines Members sichtbar und zugreifbar sind, wann immer der Member selbst sichtbar und zugreifbar ist. Ein öffentliches Ereignis, das außerhalb der Assembly sichtbar ist, soll z. B. über kein Argument verfügen, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Der Typ eines Ereignishandlers muss über einen Zugriff verfügen, der größer oder gleich dem Zugriff des Ereignishandlers ist.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Das folgende Beispiel generiert CLS01202:  
  
```  
/* CLS01202.cpp */ // compile with: /clr /LD // CLS01202 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public delegate void MyPublicDelegate(); private delegate void MyAssemblyDelegate(); public ref class One { public: event MyAssemblyDelegate^ MyEvent { public: void add(MyAssemblyDelegate^ Addparameter) {}   //  not cls compliant void remove(MyAssemblyDelegate^ Removeparameter) {}   //  not cls compliant void raise() {} } };  
```