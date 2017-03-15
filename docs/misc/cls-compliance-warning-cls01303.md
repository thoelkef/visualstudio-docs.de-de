---
title: "CLS-Kompatibilit&#228;tswarnung CLS01303 | Microsoft Docs"
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
  - "CLS01303"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01303"
ms.assetid: a8aa0cda-a2dd-41da-bcc2-53221207ea70
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS01303
Ein CLS\-kompatibles Literal muss über einen in den Feldinitialisierungsmetadaten angegebenen Wert verfügen, der mit dem Literal identisch ist \(oder den zugrunde liegenden Typ aufweist, wenn dieses Literal vom Typ „enum“ ist\).  
  
 Der Wert eines literalen statischen Elements wird von der Verwendung von Feldinitialisierungsmetadaten angegeben. Ein CLS\-kompatibles Literal muss über einen in den Feldinitialisierungsmetadaten angegebenen Wert verfügen, der mit dem Literal identisch ist \(oder den zugrunde liegenden Typ aufweist, wenn dieses Literal vom Typ „enum“ ist\).  
  
 Stellen Sie sicher, dass das Feldliteral genau den gleichen Typ wie das Literal aufweist \(oder den zugrunde liegenden Typ aufweist, wenn dieses Literal vom Typ „enum“ ist\).  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Deklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS01303 verursachen könnte:  
  
```  
.field public static literal char Field2 = int32(0x00000002)  
```  
  
 Indem Sie für den Initialisierer den gleichen Typ wire für das Literal wählen, können Sie diese Warnung beheben:  
  
```  
.field public static literal char Field2 = char(0x00000002)  
```