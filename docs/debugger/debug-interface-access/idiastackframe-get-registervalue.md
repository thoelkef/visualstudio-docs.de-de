---
title: 'Idiastackframe:: Get_registervalue | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1c08258c98b46536f17f7819ce01c296d2d1900
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459544"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Ruft den Wert eines angegebenen Registers ab, wie Sie in den Stapelrahmen gespeichert.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `registerIndex`  
 [in] Eines der [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md) Enumerationswerte.  
  
 `pRetVal`  
 [out] Der Wert in der Registrierung gespeichert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e-Enumeration](../../debugger/debug-interface-access/cv-hreg-e.md)