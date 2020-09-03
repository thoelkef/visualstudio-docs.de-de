---
title: 'IDiaSourceFile:: get_uniqueId | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e5237d8a524bd77f67c86a650bb4c8f075e407fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190626"
---
# <a name="idiasourcefileget_uniqueid"></a>IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen einfachen ganzzahligen Schlüsselwert ab, der für dieses Bild eindeutig ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt einen einfachen ganzzahligen Schlüsselwert zurück, der für dieses Bild eindeutig ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Das Vergleichen von Schlüsseln anstelle von Zeichen folgen kann die Verarbeitung von Zeilennummern beschleunigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
