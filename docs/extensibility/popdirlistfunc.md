---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702083"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Dies ist eine Rückruffunktion, die der [SccPopulateDirList-Funktion](../extensibility/sccpopulatedirlist-function.md) gegeben wird, um eine Auflistung von Verzeichnissen und (optional) Dateinamen zu aktualisieren, um herauszufinden, welche unter Quellcodeverwaltung stehen.

 Der `POPDIRLISTFUNC` Rückruf sollte nur für die Verzeichnisse und Dateinamen aufgerufen `SccPopulateDirList` werden (in der Liste, die der Funktion gegeben ist), die sich tatsächlich unter Quellcodeverwaltung befinden.

## <a name="signature"></a>Signatur

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Parameter
 pvCallerData

[in] Benutzerwert für [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

[in] `TRUE` wenn es `lpDirectoryOrFileName` sich bei dem Namen in um ein Verzeichnis handelt; Andernfalls ist der Name ein Dateiname.

 lpDirectoryOrFileName

[in] Vollständiger lokaler Pfad zu einem Verzeichnis oder Dateinamen, der sich unter Quellcodeverwaltung befindet.

## <a name="return-value"></a>Rückgabewert
 Die IDE gibt einen entsprechenden Fehlercode zurück:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Setzen Sie die Verarbeitung fort.|
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|
|SCC_E_xxx|Jeder geeignete Quellcodeverwaltungsfehler sollte die Verarbeitung beenden.|

## <a name="remarks"></a>Bemerkungen
 Wenn `fOptions` der Parameter `SccPopulateDirList` der `SCC_PDL_INCLUDEFILES` Funktion das Flag enthält, enthält die Liste möglicherweise Dateinamen sowie Verzeichnisnamen.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Fehlercodes](../extensibility/error-codes.md)
