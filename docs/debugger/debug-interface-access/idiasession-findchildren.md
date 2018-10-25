---
title: 'Idiasession:: Findchildren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 16033fc289e5a1fe2a8331e927bba51ce1671fd2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896171"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Ruft alle untergeordneten Elemente einer angegebenen übergeordneten Element-ID, die den Namen und Symbol Datentyp entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `parent`  
 [in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das das übergeordnete Element darstellt. Wenn dieses übergeordneten Symbol ist eine Funktion, Modul oder Block, in die untergeordneten lexikalischen zurückgegeben werden `ppResult`. Wenn das übergeordnete Symbol ein Typ ist, werden der untergeordneten Klasse zurückgegeben. Wenn dieser Parameter ist `NULL`, klicken Sie dann `symtag` muss festgelegt werden, um `SymTagExe` oder `SymTagNull`, die den globalen Bereich (.exe-Datei) zurückgibt.  
  
 `symtag`  
 [in] Gibt das Symboltag der untergeordneten Elemente abgerufen werden sollen. Werte stammen aus der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration. Legen Sie auf `SymTagNull` auf alle untergeordneten Elemente abzurufen.  
  
 `name`  
 [in] Gibt den Namen der untergeordneten Elemente abgerufen werden sollen. Legen Sie auf `NULL` für alle untergeordneten Elemente abgerufen werden sollen.  
  
 `compareFlags`  
 [in] Gibt die Vergleichsoptionen, die auf Namen angewendet. Werte aus der [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) -Enumeration können alleine oder zusammen verwendet werden.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt, das die Liste der untergeordneten Symbolen enthält abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die lokale Variablen der Funktion `pFunc` , namensübereinstimmung `szVarName`.  
  
```C++  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)