---
title: 'Idiasymmetribol:: get_isStripped | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isStripped method
ms.assetid: cc2c4a0b-ab9f-4b79-a8ff-a3badb0405d6
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 37fd166696d8fbcc913f26fb654ea5e709eb3a3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841047"
---
# <a name="idiasymbolget_isstripped"></a>IDiaSymbol::get_isStripped
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft das Flag ab, das angibt, ob Private Symbole aus der Symbol Datei entfernt wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_isStripped(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 vorgenommen Gibt zurück, `TRUE` Wenn Private Symbole aus der Symbol Datei entfernt wurden; andernfalls wird zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft ist über den `SymTagExe` Symboltyp verfügbar (siehe [exe](../../debugger/debug-interface-access/exe.md)).  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 8.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)
