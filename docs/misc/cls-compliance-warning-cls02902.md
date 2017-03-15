---
title: "CLS-Kompatibilit&#228;t: Warnung CLS02902 | Microsoft Docs"
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
  - "CLS02902"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS02902"
ms.assetid: 028c91fc-d3bb-4c97-92e6-159b5d663fc2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS-Kompatibilit&#228;t: Warnung CLS02902
Die Methoden, die ein Ereignis implementieren, müssen in den Metadaten mit "SpecialName" gekennzeichnet sein.  
  
 Eine Methode, die ein Ereignis implementiert, wurde in den Metadaten nicht mit **specialname** gekennzeichnet.  
  
 Weitere Informationen zur CLS\-Kompatibilitätsüberprüfung finden Sie unter [CLS\-kompatible Assemblys](http://msdn.microsoft.com/de-de/3320b57e-ea55-4697-a17d-f509a36a3c93).  
  
 Die folgende Funktionsdeklaration \(die die MSIL\-Assemblysprache verwendet\) zeigt, was CLS02902 verursachen könnte:  
  
```  
.method public instance void raise_MyEvent(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent  
```  
  
 Sie können diese Warnung beheben, indem Sie das **specialname**\-Schlüsselwort hinzufügen:  
  
```  
.method public specialname instance void raise_MyEvent(object __unnamed000, class [mscorlib]System.EventArgs __unnamed001) cil managed { } // end of method One::raise_MyEvent  
```