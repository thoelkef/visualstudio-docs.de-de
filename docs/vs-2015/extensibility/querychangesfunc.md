---
title: Querychangesfunc | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42f901fa31b3b682c7e19c98f5707adb3b4fb3f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193853"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dies ist eine Rückruffunktion, die vom [sccquerychanges](../extensibility/sccquerychanges-function.md) -Vorgang verwendet wird, um eine Auflistung von Dateinamen aufzulisten und den Status jeder Datei zu bestimmen.  
  
 Die `SccQueryChanges` Funktion erhält eine Liste von Dateien und einen Zeiger auf den `QUERYCHANGESFUNC` Rückruf. Das Quellcodeverwaltungs-Plug-in listet die angegebene Liste auf und gibt den Status (über diesen Rückruf) für jede Datei in der Liste an.  
  
## <a name="signature"></a>Signatur  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvcallerdata  
 in Der vom Aufrufer `pvCallerData` (IDE) an [sccquerychanges](../extensibility/sccquerychanges-function.md)übergebenen Parameter. Das Quellcodeverwaltungs-Plug-in sollte keine Annahmen über den Inhalt dieses Werts machen.  
  
 pchangesdata  
 in Ein Zeiger auf eine [querychangesdata-Struktur](#LinkQUERYCHANGESDATA) Struktur, die die Änderungen an einer Datei beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die IDE gibt einen entsprechenden Fehlercode zurück:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Setzen Sie die Verarbeitung fort.|  
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC_E_xxx|Jeder geeignete SCC-Fehler sollte die Verarbeitung verhindern.|  
  
## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Querychangesdata-Struktur  
 Die für jede Datei über gegebene Struktur sieht wie folgt aus:  
  
```cpp#  
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
 Größe dieser Struktur (in Bytes).  
  
 lpFileName  
 Der ursprüngliche Dateiname für dieses Element.  
  
 dwChangeType  
 Code, der den Status der Datei angibt:  
  
|Code|BESCHREIBUNG|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Kann nicht erkennen, was sich geändert hat.|  
|`SCC_CHANGE_UNCHANGED`|Keine Namensänderungen für diese Datei.|  
|`SCC_CHANGE_DIFFERENT`|Datei mit einer anderen Identität, aber der gleiche Name ist in der Datenbank vorhanden.|  
|`SCC_CHANGE_NONEXISTENT`|Die Datei ist weder in der Datenbank noch lokal vorhanden.|  
|`SCC_CHANGE_DATABASE_DELETED`|Die Datei wurde in der Datenbank gelöscht.|  
|`SCC_CHANGE_LOCAL_DELETED`|Die Datei wurde lokal gelöscht, die Datei ist jedoch noch in der Datenbank vorhanden. Wenn dies nicht bestimmt werden kann, geben Sie zurück `SCC_CHANGE_DATABASE_ADDED` .|  
|`SCC_CHANGE_DATABASE_ADDED`|Die Datei wurde der Datenbank hinzugefügt, ist jedoch nicht lokal vorhanden.|  
|`SCC_CHANGE_LOCAL_ADDED`|Die Datei ist nicht in der Datenbank vorhanden, und ist eine neue lokale Datei.|  
|`SCC_CHANGE_RENAMED_TO`|Die Datei wurde in die Datenbank umbenannt oder in verschoben `lpLatestName` .|  
|`SCC_CHANGE_RENAMED_FROM`|Die Datei wurde von in der Datenbank umbenannt oder in die Datenbank verschoben `lpLatestName` . wenn diese zu teuer ist, geben Sie ein anderes Flag zurück, z `SCC_CHANGE_DATABASE_ADDED` . b..|  
  
 lplatestname  
 Der aktuelle Dateiname für dieses Element.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Sccquerychanges](../extensibility/sccquerychanges-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)
