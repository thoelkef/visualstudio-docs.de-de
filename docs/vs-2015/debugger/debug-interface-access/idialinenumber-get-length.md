---
title: 'Idialinenumber:: Get_length | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79657b3f7b03d7e5884cab278cf4cc46aa123033
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823670"
---
# <a name="idialinenumbergetlength"></a>IDiaLineNumber::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Anzahl der Bytes in einem Block ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Bytes in einem Block zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Block ist die Länge des Quellcodes in der Zeile, dargestellt durch die [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



