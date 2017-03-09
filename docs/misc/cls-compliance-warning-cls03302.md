---
title: "CLS-Kompatibilit&#228;t: Warnung CLS03302 | Microsoft Docs"
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
  - "CLS03302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS03302"
ms.assetid: 3b99e64b-d5cb-4eb8-81b5-fd96992f2c10
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS03302
Ereignisse müssen einem bestimmten Benennungsschema folgen  
  
 Ereignisse müssen einem bestimmten Benennungsschema folgen. Der Name der Accessorfunktionen des Ereignisses ist identisch mit dem Ereignisnamen mit vorangestelltem **raise\_**, **remove\_** oder **add\_**.  
  
 Das **specialname**\-Attribut muss in den entsprechenden Namensvergleichen ignoriert werden und Bezeichnerregeln einhalten.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(unter Verwendung der MSIL\-Assemblysprache\) zeigt, was CLS03302 verursachen könnte:  
  
```  
.method public specialname instance void add_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::add_MyEvent .method public specialname instance void remove_MyEventaaa(class MyAssemblyDelegate __unnamed000) cil managed { } // end of method One::remove_MyEvent .method public specialname instance void raise_MyEventaaa(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent .event specialname MyAssemblyDelegate MyEvent { .addon instance void One::add_MyEventaaa(class MyAssemblyDelegate) .removeon instance void remove_MyEventaaa(class MyAssemblyDelegate) .fire instance void raise_MyEventaaa(object, class [mscorlib]System.EventArgs) } // end of event One::MyEvent } // end of class One  
```  
  
 Beachten Sie, dass die Namen der Accessormethoden sich vom Ereignisnamen unterscheiden.  Indem Sie sicherstellen, dass alle Ereignisaccessornamen dem Benennungsschema folgen, können Sie CLS03302 auflösen.