---
title: SccPopulateDirList-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74d6008db15cc8cd89daf4882d8952006dc547d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433083"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList-Funktion
Diese Funktion bestimmt, welche Verzeichnisse und (optional) die Dateien, in der quellcodeverwaltung ist eine Liste der Verzeichnisse gespeichert sind, um zu überprüfen.

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
 "pContext"

[in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.

 nDirs

[in] Anzahl der Verzeichnispfade, in der `lpDirPaths` Array.

 lpDirPaths

[in] Ein Array von Verzeichnispfaden, um zu überprüfen.

 pfnPopulate

[in] Rückruffunktion für jedes Verzeichnispfad und (optional) den Dateinamen im `lpDirPaths` (finden Sie unter [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Einzelheiten).

 pvCallerData

[in] Wert, der unverändert an die Rückruffunktion übergeben werden soll.

 Bestanden

[in] Eine Kombination von Werten, die steuern, wie die Verzeichnisse verarbeitet werden (finden Sie im Abschnitt "PopulateDirList Flags" [Bitflags, die von bestimmten Befehlen verwendete](../extensibility/bitflags-used-by-specific-commands.md) mögliche Werte).

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Der Vorgang erfolgreich abgeschlossen.|
|SCC_E_UNKNOWNERROR|Es ist ein Fehler aufgetreten.|

## <a name="remarks"></a>Hinweise
 Nur die Verzeichnisse und (optional) die Namen, die tatsächlich in das Quellcodeverwaltungs-Repository werden an die Rückruffunktion übergeben.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Fehlercodes](../extensibility/error-codes.md)