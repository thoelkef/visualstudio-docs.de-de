---
title: WriteAllTLogs | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c64f0079a03b730fb700cfbc6320c5dffa05d7a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579516"
---
# <a name="writealltlogs"></a>WriteAllTLogs
Schreibt Nachverfolgungsprotokolle für alle Threads und Kontexte

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parameter
[in] `intermediateDirectory`

 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll

[in] `tlogRootName`

 Der Stammname des Namens der Protoktolldatei

## <a name="return-value"></a>Rückgabewert
 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde

## <a name="requirements"></a>Anforderungen
 **Header:** *FileTracker.h*

## <a name="see-also"></a>Siehe auch
- [WriteContextTLogs](../msbuild/writecontexttlogs.md)