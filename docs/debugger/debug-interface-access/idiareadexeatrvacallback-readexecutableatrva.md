---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca1b1ec2bea56ad167951ad8b60cf849bd22e315
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742788"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Liest die angegebene Anzahl von Bytes ab der angegebenen relativen virtuellen Adresse (RVA) aus der ausführbaren Datei.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parameter
 `relativeVirtualAddress`

in Die RVA in der ausführbaren Datei, die gelesen werden soll.

 `cbData`

in Anzahl der zu lesenden Bytes.

 `pcbData`

vorgenommen Gibt die Anzahl der gelesenen Bytes zurück.

 `data[]`

[in, out] Ein Array, das mit aus der Datei gelesenen Bytes gefüllt ist.

## <a name="remarks"></a>Hinweise
 Diese Methode wird vom Dia-Unterstützungs Code aufgerufen, um Daten Bytes aus einer ausführbaren Datei mit einer relativen virtuellen Adresse zu laden. Diese Methode wird zur Unterstützung der [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode aufgerufen.

## <a name="see-also"></a>Siehe auch
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)