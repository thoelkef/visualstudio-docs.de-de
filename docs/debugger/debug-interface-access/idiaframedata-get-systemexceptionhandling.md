---
title: 'Idiaframedata:: Get_systemexceptionhandling | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_systemExceptionHandling method
ms.assetid: e8df1972-913c-446c-9779-775575b0caa9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 889f2cf72d27b84cff86792f7b0ba3a43d63d09e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882729"
---
# <a name="idiaframedatagetsystemexceptionhandling"></a>IDiaFrameData::get_systemExceptionHandling
Ruft ein Flag, das angibt, ob die Behandlung von Ausnahmen aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt `TRUE` ist Behandlung von Ausnahmen in Kraft ist, andernfalls gibt `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Behandlung von Ausnahmen wird häufiger als strukturierte Ausnahmebehandlung bezeichnet.  
  
 Um zu bestimmen, wenn die C++-Ausnahmebehandlung gültig ist, rufen Sie die [idiaframedata:: Get_cplusplusexceptionhandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)