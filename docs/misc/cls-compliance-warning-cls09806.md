---
title: "CLS-Kompatibilit&#228;t: Warnung CLS09806 | Microsoft Docs"
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
  - "CLS09806"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS09806"
ms.assetid: fc97cf0e-c72e-4c09-96be-f90f9840e76e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS09806
Generische Methoden sind nicht CLS\-kompatibel.  
  
 Eine generische Methode ist nicht CLS\-kompatibel.  
  
 Weitere Informationen zur Überprüfung der CLS\-Kompatibilität \(Common Language Subset\) finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS09806 generiert:  
  
```  
// CLS09806.cpp // compile with: /clr /LD /link /noentry // CLS09806 expected using namespace System::Reflection; [assembly:AssemblyKeyFile("clscompliance.snk")]; using namespace System; [assembly:CLSCompliant (true)]; generic <class T> public ref struct One { public: generic <class U> void Method1() {} };  
```