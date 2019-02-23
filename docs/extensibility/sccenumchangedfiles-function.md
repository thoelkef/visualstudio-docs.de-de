---
title: SccEnumChangedFiles-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9bc2738e9a4d7cac0d57b9c613b7070f60baff
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711556"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles-Funktion
Basierend auf einer Liste von lokalen Dateien, bestimmt diese Funktion, welche Dateien in Quellcode-Verwaltungsdatenbank Code die entsprechenden Versionen unterscheiden.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parameter
 "pContext"

[in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.

 cFiles

[in] Anzahl der im angegebenen Dateinamen der `lpFileNames` Array. Gibt auch die Größe des `plIsFileDifferent` Array.

 lpFileNames

[in] Array von Namen lokale Datei, um zu überprüfen.

 plIsFileDifferent

[in, out] Array von Werten, die den Unterschied Status jeder Datei (Array benötigen mindestens `cFiles` Einträge). Ungleich NULL bedeutet, dass die Datei unterscheidet.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Der Vorgang erfolgreich abgeschlossen wurde.|
|SCC_UNSPECIFIEDERROR|Allgemeiner Fehler.|

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)