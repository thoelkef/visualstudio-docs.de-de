---
title: "CLS-Kompatibilit&#228;tswarnung CLS00711 | Microsoft Docs"
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
  - "CLS00711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00711"
ms.assetid: 76481641-bda1-4128-8da8-ccba577b7ba1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS00711
Der zugrunde liegende Typ einer Enumeration muss ein integrierter CLS\-Ganzzahltyp sein  
  
 Wenn Sie den zugrunde liegenden Typ einer Enumeration angeben und eine CLS\-kompatible Assembly verwenden möchten, muss der zugrunde liegende Typ der Enumeration ein CLS\-kompatibler \(Common Language Subset\) Ganzzahltyp sein.  
  
 Weitere Informationen über CLS\-Enumerationen finden Sie unter [Enumerationsklasse](/visual-cpp/windows/enum-class-cpp-component-extensions).  
  
 Weitere Informationen zur CLS\-Kompatibilitätsüberprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS00711 generiert:  
  
```  
// CLS00711.cpp // compile with: /clr /LD // CLS00711 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; public ref class One { public: enum class MyEnum_cls_bad : Char { bad_one = 1, bad_two = 2, bad_three = 3 }; enum class MyEnum_cls_good : Int32 { good_one = 1, good_two = 2, good_three = 3 }; };  
```