---
title: StartTrackingContextWithRoot | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68d585361b9797bf1df9c8b0b31f8a089e9de025
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632094"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Startet einen Nachverfolgungskontext mithilfe einer Antwortdatei, die einen Stammmarker angibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Parameter

[in] `intermediateDirectory`

 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll

[in] `taskName`

 Identifiziert den Nachverfolgungskontext. Dieser Name wird verwendet, um den Protokolldateinamen zu erstellen.

[in] `rootMarkerResponseFile`

 Der Pfadname einer Antwortdatei mit einem Stammmarker. Der Stammname wird verwendet, um alle Nachverfolgungen für einen Kontext zusammen zu gruppieren.

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*

## <a name="see-also"></a>Siehe auch

- [StartTrackingContext](../msbuild/starttrackingcontext.md)