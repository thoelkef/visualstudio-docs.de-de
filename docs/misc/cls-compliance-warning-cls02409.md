---
title: "CLS-Kompatibilit&#228;t: Warnung CLS02409 | Microsoft Docs"
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
  - "CLS02409"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02409"
ms.assetid: 71d566ce-59c2-4d3d-97ff-72f4e9bd21ee
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS02409
Die Methoden, mit denen die Getter\-Methode und die Setter\-Methode einer Eigenschaft implementiert werden, müssen in den Metadaten mit "SpecialName" markiert werden  
  
 Die Methoden, mit denen die Getter\-Methode und die Setter\-Methode einer Eigenschaft implementiert werden, wurden in den Metadaten nicht mit **specialname** markiert.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS02409 verursachen könnte:  
  
```  
.method public instance int32 get_MyProperty() cil managed  
```  
  
 Sie können diese Warnung vermeiden, indem Sie das **specialname**\-Schlüsselwort hinzufügen:  
  
```  
.method public specialname instance int32 get_MyProperty() cil managed  
```