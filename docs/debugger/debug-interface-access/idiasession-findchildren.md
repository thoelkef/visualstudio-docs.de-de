---
title: 'Idiasession:: Findchildren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74162d2985ea617569d4bcb250660a261528b395
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Ruft alle untergeordneten Elemente einer angegebenen übergeordneten Element-ID, die den Namen und ein Symbol Typ entsprechen.  
  
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
 [in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das das übergeordnete Element darstellt. Wenn dieses Symbol übergeordneten ist eine Funktion, einem Modul oder einem Block, werden die untergeordneten lexikalischen in zurückgegeben `ppResult`. Wenn das Symbol für übergeordnete ein Typ ist, werden die untergeordneten Klasse zurückgegeben. Wenn dieser Parameter ist `NULL`, klicken Sie dann `symtag` muss festgelegt werden, um `SymTagExe` oder `SymTagNull`, die im globalen Gültigkeitsbereich (.exe-Datei) zurückgibt.  
  
 `symtag`  
 [in] Gibt das Symboltag der untergeordneten Elemente abgerufen werden sollen. Werte stammen aus den [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration. Legen Sie auf `SymTagNull` an alle untergeordneten Elemente abzurufen.  
  
 `name`  
 [in] Gibt den Namen der untergeordneten Elemente abgerufen werden sollen. Legen Sie auf `NULL` für alle untergeordneten Elemente abgerufen werden sollen.  
  
 `compareFlags`  
 [in] Gibt die Vergleichsoptionen, die auf die namensübereinstimmung angewendet. Werte aus der [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) Enumeration kann allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt, das die Liste der untergeordneten Symbole enthält abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie lokale Variablen der Funktion gefunden `pFunc` Übereinstimmung namens `szVarName`.  
  
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