---
title: "Compilerwarnung (Stufe 1) CS0626 | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS0626
Methode, Operator oder Accessor 'Methode' ist extern markiert und weist keine Attribute auf. Erwägen Sie das Hinzufügen eines DllImport\-Attributs, um die externe Implementierung anzugeben.  
  
 Eine als `extern` gekennzeichnete Methode sollte mit einem Attribut gekennzeichnet werden, z. B. das [DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic)\-Attribut.  
  
 Das Attribut gibt an, wo die Methode implementiert wird. Diese Informationen sind zur Laufzeit des Programms erforderlich.  
  
 Im folgenden Beispiel wird CS0626 generiert:  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```