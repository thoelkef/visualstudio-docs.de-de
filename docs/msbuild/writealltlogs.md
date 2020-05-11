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
ms.openlocfilehash: 7eadb30ee25b1182be5deb12feebd5ef280ebf4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630677"
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