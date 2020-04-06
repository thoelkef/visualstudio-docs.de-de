---
title: SccEnumChangedFiles-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700903"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles-Funktion
Angesichts einer Liste lokaler Dateien bestimmt diese Funktion, welche Dateien sich von den entsprechenden Versionen in der Quellcodeverwaltungsdatenbank unterscheiden.

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
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 cFiles

[in] Anzahl der im `lpFileNames` Array angegebenen Dateinamen. Gibt auch die `plIsFileDifferent` Größe des Arrays an.

 lpFileNames

[in] Array lokaler Dateinamen, die überprüft werden sollen.

 plIsFileDifferent

[in, out] Array von Werten, die den Differenzstatus jeder Datei `cFiles` angeben (Array muss mindestens Einträge haben). Ein Wert ungleich Null bedeutet, dass die Datei anders ist.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Operation erfolgreich abgeschlossen.|
|SCC_UNSPECIFIEDERROR|Allgemeiner Fehler.|

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
