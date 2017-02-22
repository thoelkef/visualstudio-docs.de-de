---
title: "QUERYCHANGESFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "QUERYCHANGESFUNC Callback-Funktion"
  - "QUERYCHANGESDATA-Struktur"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dies ist eine Rückruffunktion, die anhand der [SccQueryChanges](../extensibility/sccquerychanges-function.md) Vorgang zum Auflisten einer Auflistung von Dateinamen und zum Bestimmen des Status jeder Datei.  
  
 Die `SccQueryChanges` Funktion empfängt eine Liste von Dateien und ein Zeiger auf die `QUERYCHANGESFUNC` Rückruf. Das Quellcodeverwaltungs\-Plug\-In durchläuft die Elemente der angegebenen Liste sowie Status \(über diesen Rückruf\) für jede Datei in der Liste.  
  
## Signatur  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## Parameter  
 pvCallerData  
 \[in\] Die `pvCallerData` übergebene Parameter vom Aufrufer \(der IDE\) [SccQueryChanges](../extensibility/sccquerychanges-function.md). Das Datenquellen\-Steuerelement, das plug\-in sollten keine Annahmen zum Inhalt dieses Werts.  
  
 pChangesData  
 \[in\] Zeiger auf eine [QUERYCHANGESDATA-Struktur](#LinkQUERYCHANGESDATA) \-Struktur, die die Änderungen an einer Datei beschreibt.  
  
## Rückgabewert  
 Die IDE gibt einen geeigneten Fehlercode zurück:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Verarbeitung fortgesetzt.|  
|SCC\_I\_OPERATIONCANCELED|Beendet die Verarbeitung.|  
|SCC\_E\_xxx|Alle entsprechenden SCC\-Fehler soll Verarbeitung beendet werden.|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA\-Struktur  
 Die für jede Datei übergebene Struktur sieht folgendermaßen aus:  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 Die Größe dieser Struktur \(in Byte\).  
  
 lpFileName  
 Der ursprüngliche Dateiname für dieses Element.  
  
 dwChangeType  
 Code, der Status der Datei angibt:  
  
|Code|Beschreibung|  
|----------|------------------|  
|`SCC_CHANGE_UNKNOWN`|Kann nicht feststellen, was sich geändert hat.|  
|`SCC_CHANGE_UNCHANGED`|Keine Änderungen für diese Datei.|  
|`SCC_CHANGE_DIFFERENT`|Datei mit einer anderen Identität jedoch der gleiche Namen in der Datenbank vorhanden ist.|  
|`SCC_CHANGE_NONEXISTENT`|Datei existiert nicht in der Datenbank oder lokal.|  
|`SCC_CHANGE_DATABASE_DELETED`|Datei, die in der Datenbank gelöscht werden.|  
|`SCC_CHANGE_LOCAL_DELETED`|Datei lokal gelöscht, aber die Datei immer noch vorhanden in der Datenbank. Wenn dies nicht bestimmt werden kann, zurück `SCC_CHANGE_DATABASE_ADDED`.|  
|`SCC_CHANGE_DATABASE_ADDED`|Datei der Datenbank hinzugefügt, aber es ist nicht lokal vorhanden.|  
|`SCC_CHANGE_LOCAL_ADDED`|Datei in der Datenbank nicht vorhanden, und es ist eine neue lokale Datei.|  
|`SCC_CHANGE_RENAMED_TO`|Datei umbenannt oder verschoben werden, in der Datenbank als `lpLatestName`.|  
|`SCC_CHANGE_RENAMED_FROM`|Datei umbenannt oder verschoben werden, in der Datenbank `lpLatestName`; Wenn dies zu teuer, nachzuverfolgen, zurückgeben Kennzeichens, wie z. B. `SCC_CHANGE_DATABASE_ADDED`.|  
  
 lpLatestName  
 Der aktuelle Dateiname für dieses Element.  
  
## Siehe auch  
 [Callback\-Funktionen, die von der IDE implementiert](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [Fehlercodes](../extensibility/error-codes.md)