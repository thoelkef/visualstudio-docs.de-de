---
title: 'Idiasymmetribol:: get_oemSymbolId | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4031672840237b0496ba7c6dbb9bb3b1658d7023
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842303"
---
# <a name="idiasymbolget_oemsymbolid"></a>IDiaSymbol::get_oemSymbolId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den ID-Wert des Originalgeräte Herstellers (OEM) ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_oemSymbolId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt die intern zugewiesene Symbol-ID eines OEM zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Bezeichner ist ein eindeutiger Wert, der vom Dia SDK erstellt wird, um alle Symbole als eindeutig zu markieren.  
  
 Diese Eigenschaft gilt nur für Symbole mit einem [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) -Enumerationstyp von `SymTagCustomType` .  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
