---
title: 'IDiaStackFrame:: get_size | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_size method
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0f646dd6bfe93835d2d30280c7e57e7de2fbefa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190507"
---
# <a name="idiastackframeget_size"></a>IDiaStackFrame::get_size
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Größe des Stapel Rahmens in Bytes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_size (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die Größe des Stapel Rahmens in Bytes zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn die Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
