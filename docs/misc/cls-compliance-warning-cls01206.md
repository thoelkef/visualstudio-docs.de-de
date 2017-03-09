---
title: "CLS-Kompatibilit&#228;tswarnung CLS01206 | Microsoft Docs"
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
  - "CLS01206"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01206"
ms.assetid: e72f2293-874b-406c-9f22-92aeb64ac732
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01206
Die Sichtbarkeit und der Zugriff von Typen und Membern soll so beschaffen sein, dass Typen in der Signatur eines Members sichtbar und zugreifbar sind, wann immer der Member selbst sichtbar und zugreifbar ist. Zum Beispiel soll eine öffentliche Memberfunktion, die außerhalb der Assembly sichtbar ist, über kein Argument verfügen, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Typen in Methodensignaturen müssen eine größere oder gleiche Zugreifbarkeit wie die Methode aufweisen.  Zum Beispiel soll eine öffentliche Methode, die außerhalb der Assembly sichtbar ist, über kein Argument verfügen, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Das folgende Beispiel generiert CLS01206:  
  
```  
/* CLS01206.cpp */ // compile with: /clr /LD // CLS01206 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class PublicLevelType {}; private ref class AssemblyLevelType {}; public ref class One { public: AssemblyLevelType^ Method1() { return gcnew AssemblyLevelType(); } };  
```