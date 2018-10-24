---
title: 'Idiainjectedsource:: Get_sourcecompression | Microsoft-Dokumentation'
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
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71b1e23f9a5a5c87bbb4a789362f62dcefa06be5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879349"
---
# <a name="idiainjectedsourcegetsourcecompression"></a>IDiaInjectedSource::get_sourceCompression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Indikator verwendeten Komprimierungstyp für die Datenquelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Indikator verwendeten Komprimierungstyp für die Quelle zurück. Der Wert 0 (null) gibt an, dass keine Komprimierung der Datenquelle verwendet wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der von dieser Methode zurückgegebene Wert ist spezifisch für den Compiler verwendet. Beispielsweise kann ein Compiler Run-Length-Codierung oder Huffman-Stil-Komprimierung verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



