---
title: QUERYCHANGESFUNC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2da455cdafc399b64fe42109c7973185ce69c79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Dies ist eine Rückruffunktion, die verwendet werden, indem Sie die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Vorgang aufzählen einer Auflistung von Dateinamen, und Bestimmen des Status jeder Datei.  
  
 Die `SccQueryChanges` Funktion empfängt eine Liste von Dateien und ein Zeiger auf die `QUERYCHANGESFUNC` Rückruf. Die Datenquellen-Steuerelement-Plug-in über die angegebene Liste zählt und Status (über diese Callback) für jede Datei in der Liste enthält.  
  
## <a name="signature"></a>Signatur  
  
```cpp  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvCallerData  
 [in] Die `pvCallerData` an den Aufrufer (IDE) übergebene Parameter [SccQueryChanges](../extensibility/sccquerychanges-function.md). Die Datenquellen-Steuerelements, das plug-in sollten keine Annahmen zum Inhalt dieses Werts vornehmen.  
  
 pChangesData  
 [in] Zeiger auf eine [QUERYCHANGESDATA Struktur](#LinkQUERYCHANGESDATA) Struktur, die die Änderungen an einer Datei beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die IDE wird ein entsprechenden Fehlercode zurückgegeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Setzt die Verarbeitung fort.|  
|SCC_I_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC_E_xxx|Verarbeitet beendet alle entsprechenden SCC Auftreten des Fehlers.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a>QUERYCHANGESDATA-Struktur  
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
  
 dwSize  
 Die Größe dieser Struktur (in Byte).  
  
 lpFileName  
 Der ursprüngliche Dateiname für dieses Element.  
  
 dwChangeType  
 Code, der angibt, der Status der Datei:  
  
|Code|Beschreibung|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|Nicht feststellen, was sich geändert hat.|  
|`SCC_CHANGE_UNCHANGED`|Keine Änderungen des Computernamens für diese Datei.|  
|`SCC_CHANGE_DIFFERENT`|Datei mit einer anderen Identität jedoch der gleiche Namen in der Datenbank vorhanden ist.|  
|`SCC_CHANGE_NONEXISTENT`|Datei ist nicht in der Datenbank oder lokal vorhanden.|  
|`SCC_CHANGE_DATABASE_DELETED`|Die Datei in der Datenbank gelöscht.|  
|`SCC_CHANGE_LOCAL_DELETED`|Datei, die lokal gelöscht, aber die Datei immer noch vorhanden in der Datenbank. Wenn dies nicht bestimmt werden kann, zurück `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Datei der Datenbank hinzugefügt, aber es ist nicht lokal vorhanden.|  
|`SCC_CHANGE_LOCAL_ADDED`|Datei in Datenbank nicht vorhanden, und es wird eine neue lokale Datei.|  
|`SCC_CHANGE_RENAMED_TO`|Datei umbenannt oder verschoben werden, in der Datenbank als `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Datei umbenannt oder verschoben werden, in der Datenbank aus `lpLatestName`; Wenn dies zu verfolgen, teuer ist zurückgeben Kennzeichens, z. B. `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Der aktuelle Dateiname für dieses Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückruffunktionen implementiert, die von der IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)