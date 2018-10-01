---
title: 'Idiaframedata:: Get_lengthprolog | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaFrameData::get_lengthProlog method
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa5d37bd833879addfea5421d7ac73dc80f6a473
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522805"
---
# <a name="idiaframedatagetlengthprolog"></a>IDiaFrameData::get_lengthProlog
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaframedata:: Get_lengthprolog](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-lengthprolog).  
  
Ruft die Anzahl der Bytes der Prolog-Code im Block.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl von Bytes des prologcodes.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Prolog-Code ist eine Sequenz von Anweisungen, die beibehalten von Registern, legt den CPU-Status und den Stapel für die Funktion richtet.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



