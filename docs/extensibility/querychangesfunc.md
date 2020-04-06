---
title: QUERYCHANGESFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701635"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Dies ist eine Rückruffunktion, die vom [SccQueryChanges-Vorgang](../extensibility/sccquerychanges-function.md) verwendet wird, um eine Auflistung von Dateinamen aufzulisten und den Status jeder Datei zu bestimmen.

 Die `SccQueryChanges` Funktion erhält eine Liste von Dateien `QUERYCHANGESFUNC` und einen Zeiger auf den Rückruf. Das Quellcodeverwaltungs-Plug-In zählt über die angegebene Liste auf und stellt den Status (über diesen Rückruf) für jede Datei in der Liste bereit.

## <a name="signature"></a>Signatur

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parameter
 pvCallerData

[in] Der `pvCallerData` Parameter, der vom Aufrufer (der IDE) an [SccQueryChanges](../extensibility/sccquerychanges-function.md)übergeben wird. Das Quellcodeverwaltungs-Plug-In sollte keine Annahmen über den Inhalt dieses Werts treffen.

 pChangesData

[in] Zeiger auf eine [QUERYCHANGESDATA-Strukturstruktur,](#LinkQUERYCHANGESDATA) die die Änderungen an einer Datei beschreibt.

## <a name="return-value"></a>Rückgabewert
 Die IDE gibt einen entsprechenden Fehlercode zurück:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Setzen Sie die Verarbeitung fort.|
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|
|SCC_E_xxx|Jeder geeignete SCC-Fehler sollte die Verarbeitung beenden.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA-Struktur
 Die für jede Datei übergebene Struktur sieht wie folgt aus:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize Größe dieser Struktur (in Bytes).

 lpFileName Der ursprüngliche Dateiname für dieses Element.

 dwChangeType-Code, der den Status der Datei angibt:

|Code|BESCHREIBUNG|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Kann nicht sagen, was sich geändert hat.|
|`SCC_CHANGE_UNCHANGED`|Für diese Datei wurden keine Namen geändert.|
|`SCC_CHANGE_DIFFERENT`|Datei mit einer anderen Identität, aber derselbe Name ist in der Datenbank vorhanden.|
|`SCC_CHANGE_NONEXISTENT`|Die Datei ist weder in der Datenbank noch lokal vorhanden.|
|`SCC_CHANGE_DATABASE_DELETED`|Datei in der Datenbank gelöscht.|
|`SCC_CHANGE_LOCAL_DELETED`|Die Datei wurde lokal gelöscht, aber die Datei ist weiterhin in der Datenbank vorhanden. Wenn dies nicht `SCC_CHANGE_DATABASE_ADDED`bestimmt werden kann, kehren Sie zurück.|
|`SCC_CHANGE_DATABASE_ADDED`|Datei, die der Datenbank hinzugefügt wurde, aber lokal nicht vorhanden ist.|
|`SCC_CHANGE_LOCAL_ADDED`|Die Datei ist in der Datenbank nicht vorhanden und stellt eine neue lokale Datei vor.|
|`SCC_CHANGE_RENAMED_TO`|Datei umbenannt oder in der `lpLatestName`Datenbank als verschoben.|
|`SCC_CHANGE_RENAMED_FROM`|Datei umbenannt oder in der `lpLatestName`Datenbank von verschoben; Wenn dies zu teuer zum Nachverfolgen ist, geben Sie ein anderes Flag zurück, z. `SCC_CHANGE_DATABASE_ADDED`B. .|

 lpLatestName Der aktuelle Dateiname für dieses Element.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Fehlercodes](../extensibility/error-codes.md)
