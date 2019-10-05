---
title: IDiaSession::findInlineesByName | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9860336d-f703-4ecb-bfc4-3f5beb175a76
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c2b540303c3f31f7f6088f2ab9721b1237efbac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68151685"
---
# <a name="idiasessionfindinlineesbyname"></a>IDiaSession::findInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine Enumeration, die erlaubt einem Client, durchlaufen die Zeilennummerninformationen aller Inline-Funktionen, die mit den angegebenen Namen übereinstimmen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT findInlineesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `name`  
 [in] Gibt den Namen für den Vergleich verwendet.  
  
 `option`  
 [in] Gibt die Vergleichsoptionen, die angewendet werden, um Namen zu suchen. Werte aus der [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) -Enumeration können alleine oder zusammen verwendet werden.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) Objekt, das eine Liste neben den Zeilennummern enthält, die abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
