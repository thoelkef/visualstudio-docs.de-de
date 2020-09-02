---
title: 'IDiaSession:: findChildren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150424"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft alle untergeordneten Elemente eines angegebenen übergeordneten Bezeichners ab, die dem Namen und dem Symboltyp entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das das übergeordnete Element darstellt. Wenn dieses übergeordnete Symbol eine Funktion, ein Modul oder ein Block ist, werden die lexikalischen untergeordneten Elemente in zurückgegeben `ppResult` . Wenn das übergeordnete Symbol ein Typ ist, werden die untergeordneten Klassen der Klasse zurückgegeben. Wenn dieser Parameter ist `NULL` , `symtag` muss auf oder festgelegt `SymTagExe` werden `SymTagNull` , wodurch der globale Gültigkeitsbereich (. exe-Datei) zurückgegeben wird.  
  
 `symtag`  
 in Gibt das symboltag der untergeordneten Elemente an, die abgerufen werden sollen. Werte werden aus der Enumeration der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) entnommen. Legen Sie auf fest, `SymTagNull` um alle untergeordneten Elemente abzurufen.  
  
 `name`  
 in Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen. Legen Sie auf fest, `NULL` damit alle untergeordneten Elemente abgerufen werden.  
  
 `compareFlags`  
 in Gibt die auf die namens Übereinstimmung angewendeten Vergleichs Optionen an Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 vorgenommen Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt zurück, das die Liste der abgerufenen untergeordneten Symbole enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie lokale Variablen der Funktion gefunden werden `pFunc` , die mit dem Namen identisch sind `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
