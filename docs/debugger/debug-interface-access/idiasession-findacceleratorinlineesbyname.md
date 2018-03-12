---
title: IDiaSession::findAcceleratorInlineesByName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 084fa6d3021e7657ae0aef639a110450ed9f083d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Gibt eine Enumeration von Symbolen für Inlineframes, den Namen der angegebenen Inline-Funktion entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `name`  
 [in] Der zu durchsuchenden Inlinee-Funktionsname.  
  
 `option`  
 [in] Die Name-Suchoptionen beim Suchen nach Inline, die Frames zu verwendende entsprechen `name`. Weitere Informationen finden Sie unter [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Ein Zeiger auf ein `IDiaEnumSymbols` Schnittstellenzeiger, der mit dem Ergebnis initialisiert wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion sucht Inlinees nur innerhalb von Accelerator-Stub-Funktionen. Systemeigene C++-Prozedur Datensätze werden ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)