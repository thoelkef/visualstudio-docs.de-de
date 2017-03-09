---
title: "CLS-Kompatibilit&#228;tswarnung CLS00211 | Microsoft Docs"
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
  - "CLS00211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS00211"
ms.assetid: 3a103f6f-bfb7-42ed-83ab-1c0f34fb9672
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS00211
Member von Typen, die nicht CLS\-kompatibel sind, dürfen nicht als CLS\-kompatibel gekennzeichnet werden  
  
 Wenn ein Typ als nicht CLS\-kompatibel gekennzeichnet ist, können Typmember nicht CLS\-kompatibel gekennzeichnet werden.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS00211 generiert:  
  
```  
// CLS00211.cpp // compile with: /clr /LD // CLS00211 expected using namespace System; using namespace System::Reflection; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public ref class One { public: [CLSCompliant(true)]   // CLS00211 void X() {} };  
```