---
title: CV_call_e | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841093"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt die Aufruf Konvention für eine Funktion an.  
  
> [!NOTE]
> Nur die am häufigsten aufgelisteten Enumerationswerte werden hier dokumentiert. Die gesamte Enumeration ist in der Header Datei "cvrest. h" verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Elemente  
 CV_CALL_NEAR_C  
 Gibt eine Funktionsaufruf Konvention mit einem Push von rechts nach links an. Die Aufruf Funktion löscht den Stapel.  
  
 CV_CALL_NEAR_FAST  
 Gibt eine Funktionsaufruf Konvention mit einem Push von links nach rechts mit Registern an. Die aufgerufene Funktion verwendet die Summe der Parameter bytes, um den Stapel zu löschen.  
  
 CV_CALL_NEAR_STD  
 Gibt eine Funktionsaufruf Konvention mithilfe eines fast standardmäßigen Aufrufs an (von rechts nach links).  
  
 CV_CALL_NEAR_SYS  
 Gibt eine Funktionsaufruf Konvention mithilfe eines near-Systemaufrufs an.  
  
 CV_CALL_THISCALL  
 Gibt eine Funktionsaufruf Konvention mithilfe `this` des Aufrufs `this` an (Zeiger übergebenen Register).  
  
 CV_CALL_CLRCALL  
 Gibt eine Funktionsaufruf Konvention an, die von der Common Language Runtime (CLR) verwendet wird (auch bekannt als Aufruf Konvention mit verwaltetem Code).  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
