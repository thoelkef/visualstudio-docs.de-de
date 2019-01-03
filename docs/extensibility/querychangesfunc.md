---
title: QUERYCHANGESFUNC | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a50de0f08f5e31404a6dbe2cbf3a268ee53cc69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855009"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Dies ist eine Callback-Funktion ein, die die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Vorgang zum Aufzählen einer Auflistung von Dateinamen und jede Datei-Status zu ermitteln.  
  
 Die `SccQueryChanges` Funktion empfängt eine Liste von Dateien und einen Zeiger auf die `QUERYCHANGESFUNC` Rückruf. Das Quellcodeverwaltungs-Plug-in über die angegebene Liste zählt sowie Status (über diesen Rückruf) für jede Datei in der Liste.  
  
## <a name="signature"></a>Signatur  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvCallerData  
 [in] Die `pvCallerData` übergebene Parameter vom Aufrufer (der IDE von) [SccQueryChanges](../extensibility/sccquerychanges-function.md). Das Quellcodeverwaltungs-Plug-in, sollten keine Annahmen zum Inhalt dieses Werts.  
  
 pChangesData  
 [in] Zeiger auf eine [QUERYCHANGESDATA Struktur](#LinkQUERYCHANGESDATA) Struktur, die zur Beschreibung der Änderungen in einer Datei.  
  
## <a name="return-value"></a>Rückgabewert  
 Die IDE gibt einen geeigneten Fehlercode:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Verarbeitung fortgesetzt.|  
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC_E_xxx|Alle entsprechenden SCC-Fehler sollte die Verarbeitung beenden.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA-Struktur  
 Die Struktur für jede Datei übergeben, sieht folgendermaßen aus:  
  
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
  
 dwSize  
 Die Größe dieser Struktur (in Byte).  
  
 lpFileName  
 Der ursprüngliche Dateiname für dieses Element.  
  
 dwChangeType  
 Code, der angibt, der Status der Datei:  
  
|Code|Beschreibung|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Nicht erkennen, was sich geändert hat.|  
|`SCC_CHANGE_UNCHANGED`|Keine Änderungen des Computernamens für diese Datei.|  
|`SCC_CHANGE_DIFFERENT`|Datei mit einer anderen Identität jedoch der gleiche Namen vorhanden ist, in der Datenbank.|  
|`SCC_CHANGE_NONEXISTENT`|Datei ist nicht in der Datenbank oder lokal vorhanden.|  
|`SCC_CHANGE_DATABASE_DELETED`|Datei, die in der Datenbank gelöscht werden.|  
|`SCC_CHANGE_LOCAL_DELETED`|Datei, die lokal gelöscht, aber die Datei immer noch vorhanden in der Datenbank. Wenn nicht bestimmt werden kann, zurück `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Datei der Datenbank hinzugefügt, aber es ist nicht lokal vorhanden.|  
|`SCC_CHANGE_LOCAL_ADDED`|Datei in der Datenbank nicht vorhanden, und es wird eine neue lokale Datei.|  
|`SCC_CHANGE_RENAMED_TO`|Datei umbenannt oder verschoben werden, in der Datenbank als `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Datei umbenannt oder verschoben werden, in der Datenbank über `lpLatestName`; Wenn dies nachzuverfolgen, zu teuer geworden ist, zurück Kennzeichens, wie z. B. `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Der aktuelle Dateiname für dieses Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)