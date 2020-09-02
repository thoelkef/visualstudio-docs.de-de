---
title: 'Idiainjetedsource:: get_sourceCompression | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e8cafcaf3d245ac2310b93c16812327c381854d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192436"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Indikator der verwendeten Quell Komprimierung ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den Indikator der verwendeten Quell Komprimierung zurück. Der Wert 0 (null) gibt an, dass keine Quell Komprimierung verwendet wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der von dieser Methode zurückgegebene Wert ist spezifisch für den verwendeten Compiler. Ein Compiler kann z. b. die Codierung der Lauf Zeit Länge oder der im Huffman-Stil verwendeten Komprimierung verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
