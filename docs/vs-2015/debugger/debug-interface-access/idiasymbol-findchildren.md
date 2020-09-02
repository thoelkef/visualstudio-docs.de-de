---
title: 'Idiasymmetribol:: findChildren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a09a62a2e6b94dbccda3afce4bdd286270149c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150033"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die untergeordneten Elemente des Symbols ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `symtag`  
 in Gibt die Symbol Tags der untergeordneten Elemente an, die abgerufen werden sollen, wie in der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)definiert. Legen Sie auf fest, `SymTagNull` damit alle untergeordneten Elemente abgerufen werden.  
  
 `name`  
 in Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen. Legen Sie auf fest, `NULL` damit alle untergeordneten Elemente abgerufen werden.  
  
 `compareFlags`  
 in Gibt die auf die namens Übereinstimmung angewendeten Vergleichs Optionen an Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 vorgenommen Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt zurück, das eine Liste der abgerufenen untergeordneten Symbole enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, wenn mindestens ein untergeordnetes Element `S_OK` des Symbols gefunden wurde, oder gibt zurück, wenn keine untergeordneten Elemente `S_FALSE` gefunden wurden; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist identisch mit dem Aufruf der [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) -Methode mit diesem Symbol als ersten Parameter.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)
