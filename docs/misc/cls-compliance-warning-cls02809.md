---
title: "CLS-Kompatibilit&#228;tswarnung CLS02809 | Microsoft Docs"
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
  - "CLS02809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02809"
ms.assetid: a6e7b8e5-1587-437e-9d07-8a32fc5c4842
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;tswarnung CLS02809
Eigenschaften müssen einem bestimmten Benennungsschema folgen.  
  
 Eigenschaften müssen einem bestimmten Benennungsschema folgen. Der Name der Accessorfunktionen der Eigenschaft ist identisch mit dem Eigenschaftsnamen mit vorangestelltem **get\_** oder **set\_**.  
  
 Das **specialname**\-Attribut muss in den entsprechenden Namensvergleichen ignoriert werden und Bezeichnerregeln einhalten.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS02809 verursachen könnte:  
  
```  
.method public specialname instance void set_MyPropertya(int32 __unnamed000) cil managed { } // end of method One::set_MyProperty .method public specialname instance int32 get_MyPropertya() cil managed { } // end of method One::get_MyProperty .property instance int32 MyProperty() { .get instance int32 One::get_MyPropertya() .set instance void One::set_MyPropertya(int32) } // end of property One::MyProperty  
```  
  
 Beachten Sie, dass die Namen der Accessormethoden sich vom Eigenschaftsnamen unterscheidet.  Indem Sie sicherstellen, dass alle Eigenschaftsnamen dem Benennungsschema folgen, können Sie CLS02809 auflösen.