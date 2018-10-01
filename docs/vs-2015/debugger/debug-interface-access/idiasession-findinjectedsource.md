---
title: 'Idiasession:: Findinjectedsource | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73f40f2536b72c900e20ff49492ff741e3ca927d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512156"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasession:: Findinjectedsource](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-findinjectedsource).  
  
Ruft eine Liste der Datenquellen, die in den Symbolspeicher vom Attributanbieter abgelegt wurden, oder andere Komponenten des im Verlauf des Vorgangs ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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



