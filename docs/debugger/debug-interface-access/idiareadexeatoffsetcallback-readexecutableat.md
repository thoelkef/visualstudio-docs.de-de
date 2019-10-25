---
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d913a229dafb64570728434576716ba396648af3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742834"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Liest die angegebene Anzahl von Bytes ab dem angegebenen Offset aus einer ausführbaren Datei.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parameter
 fileOffset

in Der Offset in der ausführbaren Datei, ab dem gelesen werden soll.

 cbData

in Anzahl der zu lesenden Bytes.

 pcbData

vorgenommen Gibt die Anzahl der gelesenen Bytes zurück.

 data[]

[in, out] Ein Array, das mit aus der Datei gelesenen Bytes gefüllt ist.

## <a name="remarks"></a>Hinweise
 Diese Methode wird vom Dia-Unterstützungs Code aufgerufen, um Daten Bytes aus einer ausführbaren Datei mithilfe eines absoluten Dateioffsets zu laden. Diese Methode wird zur Unterstützung der [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode aufgerufen.

## <a name="see-also"></a>Siehe auch
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)