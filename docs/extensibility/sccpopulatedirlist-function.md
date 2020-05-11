---
title: SccPopulateDirList-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700555"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList-Funktion
Diese Funktion bestimmt, welche Verzeichnisse und (optional) Dateien in der Quellcodeverwaltung gespeichert werden, wenn eine Liste von Verzeichnissen angezeigt wird, die untersucht werden sollen.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 nDirs

[in] Anzahl der Verzeichnispfade `lpDirPaths` im Array.

 lpDirPaths

[in] Array von zu untersuchenden Verzeichnispfaden.

 pfnPopulate

[in] Rückruffunktion zum Aufrufen für jeden Verzeichnispfad und (optional) Dateinamen in `lpDirPaths` (Details siehe [POPDIRLISTFUNC).](../extensibility/popdirlistfunc.md)

 pvCallerData

[in] Wert, der unverändert an die Rückruffunktion übergeben werden soll.

 Foptions

[in] Eine Kombination von Werten, die steuern, wie die Verzeichnisse verarbeitet werden (siehe Abschnitt "PopulateDirList-Flags" von [Bitflags,](../extensibility/bitflags-used-by-specific-commands.md) die von bestimmten Befehlen verwendet werden, für mögliche Werte).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Vorgang wurde erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR|Ein Fehler ist aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Nur die Verzeichnisse und (optional) Dateinamen, die sich tatsächlich im Quellcodeverwaltungs-Repository befinden, werden an die Rückruffunktion übergeben.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Fehlercodes](../extensibility/error-codes.md)
