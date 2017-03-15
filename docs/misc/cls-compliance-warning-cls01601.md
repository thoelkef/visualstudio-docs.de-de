---
title: "CLS-Kompatibilit&#228;tswarnung CLS01601 | Microsoft Docs"
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
  - "CLS01601"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01601"
ms.assetid: fa162fc6-a0fd-4a0f-a201-4f166304d057
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01601
Arrays müssen über Elemente mit einem CLS\-kompatiblen Typ verfügen, und die Untergrenze aller Dimensionen des Arrays muss Null sein.  
  
 Arrays müssen über Elemente mit einem CLS\-kompatiblen Typ verfügen, und die Untergrenze aller Dimensionen des Arrays muss Null sein. Nur der Tatsache, dass es sich bei einem Element um ein Array handelt sowie der Elementtyp des Arrays muss zur Unterscheidung zwischen Überladungen ausreichen. Wenn das Überladen auf Grundlage mindestens zweier Arraytypen erfolgt, muss es sich bei den Elementtypen um benannte Typen handeln.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS01601 generiert:  
  
```  
// CLS01601.cpp // compile with: /clr /LD // CLS01601 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(true)] public ref class CompliantType {}; [CLSCompliant(false)] public ref class NotCompliantType {}; public ref class One { public: // CLS01601 One(array<NotCompliantType^>^ param) {} // OK One(array<CompliantType^>^ param) {} };  
```