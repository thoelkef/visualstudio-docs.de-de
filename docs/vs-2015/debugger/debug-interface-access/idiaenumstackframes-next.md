---
title: 'IDiaEnumStackFrames:: Next | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c66e8b281f27e13a1176dd32f21856367e5f1ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189745"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Stapel Rahmenelementen aus der enumerationssequenz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 in Die Anzahl der StackFrame-Elemente im Enumerator, die abgerufen werden sollen.  
  
 rgelt  
 vorgenommen Ein Array, das mit den angeforderten [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) -Objekten aufgefüllt werden soll.  
  
 pceltFetched  
 vorgenommen Gibt die Anzahl der Stapel Rahmenelemente im abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn keine Stapel Rahmen mehr vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
