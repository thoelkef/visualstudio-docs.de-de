---
title: "CLS-Kompatibilit&#228;tswarnung CLS02709 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS02709"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02709"
ms.assetid: 2dd2cf52-c602-43fa-818c-5ce90e507c79
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS02709
Der in einer Eigenschaftendeklaration verwendete Typ war nicht CLS\-kompatibel.  
  
 Alle in einer Eigenschaftendeklaration verwendeten Typen waren nicht CLS\-kompatibel.  
  
 Weitere Informationen zu Eigenschaften finden Sie unter [Eigenschaft](/visual-cpp/windows/property-cpp-component-extensions).  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS02709 generiert:  
  
```  
// CLS02709.cpp // compile with: /clr /LD // CLS02709 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { String^ LocalString; int i; public: // not CLS compliant property interior_ptr<String^> MyProperty1 { void set(interior_ptr<String^> value) {} interior_ptr<String^> get() { LocalString = "Hello"; return &LocalString; } } // CLS compliant property int MyProperty2 { void set(int value) {} int get() { i = 1; return i; } } };  
```