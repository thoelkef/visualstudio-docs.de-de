---
title: "CLS-Kompatibilit&#228;t: Warnung CLS01703 | Microsoft Docs"
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
  - "CLS01703"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01703"
ms.assetid: b03ae369-3c4b-4080-9b78-4c9bfba581a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS01703
Nicht verwaltete Zeigertypen sind nicht CLS\-kompatibel.  
  
 Ein CLS\-kompatibles Feld darf keine systemeigene Zeigerdeklaration enthalten.  
  
 Weitere Informationen zur Überprüfung der CLS\-Kompatibilität \(Common Language Subset\) finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS01703 generiert:  
  
```  
// CLS01703.cpp // compile with: /clr /LD // CLS01703 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class MyClass { public: int* Parameter;   // CLS01703 };  
```