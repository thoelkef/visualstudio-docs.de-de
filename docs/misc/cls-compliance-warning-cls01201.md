---
title: "CLS-Kompatibilit&#228;t: Warnung CLS01201 | Microsoft Docs"
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
  - "CLS01201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01201"
ms.assetid: 8c3e6ce4-8ea5-487a-bbed-56a36eceb024
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS01201
Die Sichtbarkeit und der Zugriff von Typen und Membern soll so beschaffen sein, dass Typen in der Signatur eines Members sichtbar und zugreifbar sind, wann immer der Member selbst sichtbar und zugreifbar ist. Beispielsweise darf ein öffentlicher Konstruktor, der außerhalb der Assembly sichtbar ist, kein Argument haben, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Typen in Konstruktorsignaturen müssen eine größere oder gleiche Zugreifbarkeit wie der Konstruktor aufweisen.  Beispielsweise darf ein öffentlicher Konstruktor, der außerhalb der Assembly sichtbar ist, kein Argument haben, dessen Typ nur innerhalb der Assembly sichtbar ist.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsüberprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS01201 generiert:  
  
```  
/* CLS01201.cpp */ // compile with: /clr /LD // CLS01201 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; private ref class AssemblyLevelType {}; public ref class One { public: One(AssemblyLevelType^ parameter) {}   // not cls compliant }; private value class Two { public: Two(AssemblyLevelType^ parameter) {}   // OK };  
```