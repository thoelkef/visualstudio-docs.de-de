---
title: "CLS-Kompatibilit&#228;t: Warnung CLS01603 | Microsoft Docs"
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
  - "CLS01603"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01603"
ms.assetid: 608ff6e6-8669-4cc7-a85f-5b6915ee38d5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS01603
Arrays müssen über Elemente mit einem CLS\-kompatiblen Typ verfügen, und die Untergrenze aller Dimensionen des Arrays muss Null sein.  
  
 Arrays müssen über Elemente mit einem CLS\-kompatiblen Typ verfügen, und die Untergrenze aller Dimensionen des Arrays muss Null sein. Nur der Tatsache, dass es sich bei einem Element um ein Array handelt sowie der Elementtyp des Arrays muss zur Unterscheidung zwischen Überladungen ausreichen. Wenn das Überladen auf Grundlage mindestens zweier Arraytypen erfolgt, muss es sich bei den Elementtypen um benannte Typen handeln.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Im folgenden Beispiel wird CLS01603 generiert:  
  
```  
// CLS01603.cpp // compile with: /clr /LD // CLS01603 expected using namespace System; using namespace System::Reflection; using namespace cli::language; [assembly:CLSCompliant (true)]; [assembly:AssemblyKeyFile("clscompliance.snk")]; [CLSCompliant(false)] public delegate void MyDelegate(Object ^ sender, EventArgs^ e); public delegate void MyDelegate2(Object ^ sender, EventArgs^ e); public ref struct One { array<MyDelegate^>^ MyArray;   // CLS01603 array<MyDelegate2^>^ MyArray2;   // OK };  
```