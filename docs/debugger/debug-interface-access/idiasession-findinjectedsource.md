---
title: 'Idiasession:: Findinjectedsource | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a16e3827999d165f0d04b803e4d0611bf4f2538d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53851994"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Ruft eine Liste der Datenquellen, die in den Symbolspeicher vom Attributanbieter abgelegt wurden, oder andere Komponenten des im Verlauf des Vorgangs ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 srcFile  
 [in] Name der Quelldatei nach dem gesucht werden soll.  
  
 ppResult  
 [out] Gibt eine [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) Objekt, das eine Liste mit allen eingefügten Quellen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)