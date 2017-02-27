---
title: "SccQueryInfo-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccQueryInfo"
helpviewer_keywords: 
  - "SccQueryInfo-Funktion"
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# SccQueryInfo-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft die Statusinformationen für eine Gruppe von ausgewählten Dateien unter Versionskontrolle ab.  
  
## Syntax  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 nFiles  
 \[in\] Anzahl der angegebenen Dateien in der `lpFileNames` Arrays und die Länge der `lpStatus` Array.  
  
 lpFileNames  
 \[in\] Ein Array von Namen von Dateien, die abgefragt werden.  
  
 lpStatus  
 \[in, out\] Ein Array, in dem das Quellcodeverwaltungs\-Plug\-in die Statusflags für jede Datei zurückgibt. Weitere Informationen finden Sie unter [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Abfrage war erfolgreich.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem mit dem Zugriff auf das Quellcodeverwaltungssystem wahrscheinlich durch Probleme mit dem Netzwerk oder Konflikte verursacht. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_PROJNOTOPEN|Das Projekt ist nicht in der quellcodeverwaltung geöffnet.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Wenn `lpFileName` ist eine leere Zeichenfolge, es gibt derzeit keine Statusinformationen aktualisieren. Andernfalls ist es der vollständige Pfadname der Datei für die die Statusinformationen geändert haben kann.  
  
 Die zurückgegebenen Array kann eine Bitmaske der `SCC_STATUS_xxxx` Bits. Weitere Informationen finden Sie unter [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md). Ein Quellcodeverwaltungssystem möglicherweise nicht alle Bitdatentypen unterstützt. Zum Beispiel wenn `SCC_STATUS_OUTOFDATE` nicht angeboten wird, wird das Bit nicht festgelegt ist.  
  
 Beachten Sie Folgendes, wenn diese Funktion zum Auschecken der Dateien, `MSSCCI` Status Anforderungen:  
  
-   `SCC_STATUS_OUTBYUSER` wird festgelegt, wenn der aktuelle Benutzer die Datei ausgecheckt hat.  
  
-   `SCC_STATUS_CHECKEDOUT` kann nicht festgelegt werden, es sei denn, `SCC_STATUS_OUTBYUSER` festgelegt ist.  
  
-   `SCC_STATUS_CHECKEDOUT` wird nur festgelegt, wenn die Datei in das Arbeitsverzeichnis festgelegten ausgecheckt ist.  
  
-   Wenn die Datei vom aktuellen Benutzer in einem anderen Verzeichnis als das Arbeitsverzeichnis ausgecheckt ist `SCC_STATUS_OUTBYUSER` festgelegt ist, aber `SCC_STATUS_CHECKEDOUT` nicht.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md)