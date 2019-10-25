---
title: 'IDiaSession:: findInjectedSource | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2145c90c25c448880e51b9b394c7085e0d49b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742257"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
Ruft eine Liste der Quellen ab, die von Attribut Anbietern oder anderen Komponenten des Kompilierungsprozesses in den Symbol Speicher eingefügt wurden.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>Parameter
 srcFile

in Der Name der Quelldatei, nach der gesucht werden soll.

 ppResult

vorgenommen Gibt ein [idiaenuminjetedsources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) -Objekt zurück, das eine Liste aller injizierten Quellen enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)