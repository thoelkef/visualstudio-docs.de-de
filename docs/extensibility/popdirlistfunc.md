---
title: POPDIRLISTFUNC | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 259ada240d81b87d2d36e12cddcc28efe8d893f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806095"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Dies ist eine Callback-Funktion übergeben, um die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Funktion zum Aktualisieren einer Sammlung von Verzeichnissen und (optional) um Dateinamen, um herauszufinden, die unter quellcodeverwaltung stehen.

 Die `POPDIRLISTFUNC` Rückruf aufgerufen werden soll, nur für die Verzeichnisse und Dateinamen (in der Liste übergeben, um die `SccPopulateDirList` Funktion), die tatsächlich unter quellcodeverwaltung stehen.

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

[in] Benutzerwert [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 auf bOrdneroptionen

[in] `TRUE` Wenn der Name in `lpDirectoryOrFileName` ist ein Verzeichnis; andernfalls ist der Name ein Dateiname.

 lpDirectoryOrFileName

[in] Vollständige lokale Pfad zu einem Verzeichnis oder Datei Namen, unter quellcodeverwaltung befindet.

## <a name="return-value"></a>Rückgabewert
 Die IDE gibt einen geeigneten Fehlercode:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Verarbeitung fortgesetzt.|
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|
|SCC_E_xxx|Ein Fehler der entsprechenden Quelle-Steuerelement sollte beendet die Verarbeitung.|

## <a name="remarks"></a>Hinweise
 Wenn die `fOptions` Parameter der `SccPopulateDirList` -Funktion enthält die `SCC_PDL_INCLUDEFILES` gekennzeichnet, und klicken Sie dann die Liste möglicherweise Dateinamen und Verzeichnisnamen enthalten wird.

## <a name="see-also"></a>Siehe auch
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Fehlercodes](../extensibility/error-codes.md)