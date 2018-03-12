---
title: 'Idiasession:: FindFile | Microsoft Docs'
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
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 99f3d58b444f2bf360c76dcd5f95b03ac50f7e32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Ruft die Quelldateien von Kompiliereinheit und Namen ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCompiland`  
 [in] Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das der Kompiliereinheit als einem Kontext verwendet werden, für die Suche darstellt. Legen Sie diesen Parameter, um `NULL` in jeder Kompiliereinheit Quelldateien gefunden.  
  
 `name`  
 [in] Gibt den Namen der Quelldatei abgerufen werden sollen. Legen Sie diesen Parameter, um `NULL` für alle Quelldateien abgerufen werden sollen.  
  
 `option`  
 [in] Gibt die Vergleichsoptionen, die auf den Namen suchen angewendet. Werte aus der [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md) Enumeration kann allein oder in Kombination verwendet werden.  
  
 `ppResult`  
 [out] Gibt eine [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) -Objekt, das eine Liste der Quelldateien enthält abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)