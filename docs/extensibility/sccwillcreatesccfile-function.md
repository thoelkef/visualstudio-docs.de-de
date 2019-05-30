---
title: SccWillCreateSccFile-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dc7b9f5b298260b2bcca88c75087059bd8f0065
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338453"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile-Funktion
Diese Funktion bestimmt, ob das Quellcodeverwaltungs-Plug-in die Erstellung der MSSCCPRJ unterstützt. SCC-Datei für jede der angegebenen Dateien.

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
 "pContext"

[in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.

 nFiles

[in] Die Anzahl der in enthalten die Namen der `lpFileNames` sowie die Länge des Arrays der `pbSccFiles` Array.

 lpFileNames

[in] Ein Array von vollqualifizierten Dateinamen, um zu überprüfen (Arrays muss vom Aufrufer zugeordnet werden).

 pbSccFiles

[in, out] Array, in dem Sie die Ergebnisse speichern.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Erfolgreich.|
|SCC_E_INVALIDFILEPATH|Einer der Pfade im Array ist ungültig.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Diese Funktion wird aufgerufen, mit einer Liste von Dateien, um festzustellen, ob das Quellcodeverwaltungs-Plug-in-Unterstützung in den MSSCCPRJ bietet. SCC-Datei für jede der angegebenen Dateien (für Weitere Informationen zu den MSSCCPRJ. SCC-Datei finden Sie unter [MSSCCPRJ. SCC-Datei](../extensibility/mssccprj-scc-file.md)). Quellcodeverwaltungs-Plug-ins können deklariert werden, ob sie die Möglichkeit zum Erstellen von MSSCCPRJ aufweisen. SCC-Dateien, indem Sie deklarieren `SCC_CAP_SCCFILE` während der Initialisierung. Das plug-in gibt `TRUE` oder `FALSE` pro Datei in die `pbSccFiles` Array, um anzugeben, die der angegebenen Dateien MSSCCPRJ aufweisen. SCC-Unterstützung. Wenn das plug-in einen Erfolgscode aus der Funktion zurückgegeben wird, werden die Werte im zurückgegeben Array berücksichtigt. Das Array wird ignoriert, bei einem Fehler.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Datei „MSSCCPRJ.SCC“](../extensibility/mssccprj-scc-file.md)