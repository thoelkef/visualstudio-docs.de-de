---
title: IDiaStackFrame::get_systemExceptionHandling | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_systemExceptionHandling
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 519602b09ea1adcf00ed534ecb22b4a082018464
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615428"
---
# <a name="idiastackframegetsystemexceptionhandling"></a>IDiaStackFrame::get_systemExceptionHandling
Ruft ein Flag, das angibt, ob die Behandlung von Ausnahmen aktiviert ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_systemExceptionHandling ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt `TRUE` Wenn Behandlung von Ausnahmen, die für diesen Frame; gültig ist, andernfalls `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` , wenn die Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 System-Ausnahmebehandlung ist auch bekannt als strukturierte Ausnahmebehandlung. Dies ist nicht dasselbe wie die C++-Ausnahmebehandlung.

 Um zu bestimmen, wenn die C++-Ausnahmebehandlung gültig ist, rufen Sie die [idiastackframe:: Get_cplusplusexceptionhandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)