---
title: CV_call_e | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ccdc9df86180883a5a3891563b22625fab4a2ad2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466382"
---
# <a name="cvcalle"></a>CV_call_e
Gibt die Aufrufkonvention für eine Funktion an.  
  
> [!NOTE]
>  Nur die am häufigsten verwendeten Enumerationswerte sind hier dokumentiert. Die vollständige Enumeration ist in der Headerdatei cvconst.h verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elements  
 CV_CALL_NEAR_C  
 Gibt eine Funktion Aufrufkonvention, die mithilfe eines near rechts-nach-links-Pushabonnements an. Die aufrufende Funktion löscht den Stapel.  
  
 CV_CALL_NEAR_FAST  
 Gibt eine Funktion Aufrufkonvention Register mit einem near links-nach-rechts-Push an. Die aufgerufene Funktion verwendet die Summe der Parameter Bytes auf um den Stapel zu löschen.  
  
 CV_CALL_NEAR_STD  
 Gibt eine Funktion Aufrufkonvention, die über einen nahezu standard-Aufruf (rechts-nach-links-Push).  
  
 CV_CALL_NEAR_SYS  
 Gibt eine Funktion Aufrufkonvention, die mithilfe eines near Systemaufrufs.  
  
 CV_CALL_THISCALL  
 Gibt eine Funktion aufrufen Konvention mit `this` aufrufen (`this` Zeiger in Register übergeben).  
  
 CV_CALL_CLRCALL  
 Gibt eine Funktion Aufrufkonvention, die von der Common Language Runtime (CLR) (auch bekannt als ein verwalteter Code Aufrufkonvention) verwendet.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_callingconvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)