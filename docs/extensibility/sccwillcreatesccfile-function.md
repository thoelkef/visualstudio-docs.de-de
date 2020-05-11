---
title: SccWillCreateSccFile-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700212"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile-Funktion
Diese Funktion bestimmt, ob das Quellcodeverwaltungs-Plug-In die Erstellung des MSSCCPRJ unterstützt. SCC-Datei für jede der angegebenen Dateien.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 nFiles

[in] Die Anzahl der im `lpFileNames` Array enthaltenen Dateinamen sowie `pbSccFiles` die Länge des Arrays.

 lpFileNames

[in] Ein Array vollqualifizierter Dateinamen, die überprüft werden sollen (Array muss vom Aufrufer zugewiesen werden).

 pbSccFiles

[in, out] Array, in dem die Ergebnisse gespeichert werden sollen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg.|
|SCC_E_INVALIDFILEPATH|Einer der Pfade im Array ist ungültig.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird mit einer Liste von Dateien aufgerufen, um zu bestimmen, ob das Quellcodeverwaltungs-Plug-In Unterstützung im MSSCCPRJ bietet. SCC-Datei für jede der angegebenen Dateien (weitere Informationen zum MSSCCPRJ. SCC-Datei, siehe [MSSCCPRJ. SCC-Datei](../extensibility/mssccprj-scc-file.md)). Quellcodeverwaltungs-Plug-Ins können deklarieren, ob sie MSSCCPRJ erstellen können. SCC-Dateien, `SCC_CAP_SCCFILE` indem sie während der Initialisierung deklariert werden. Das Plug-In `TRUE` `FALSE` gibt oder `pbSccFiles` pro Datei im Array an, welche der angegebenen Dateien MSSCCPRJ enthält. SCC-Unterstützung. Wenn das Plug-In einen Erfolgscode aus der Funktion zurückgibt, werden die Werte im Rückgabearray berücksichtigt. Bei einem Fehler wird das Array ignoriert.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)
