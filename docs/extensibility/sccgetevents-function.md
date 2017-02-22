---
title: "SccGetEvents-Funktion | Microsoft Docs"
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
  - "SccGetEvents"
helpviewer_keywords: 
  - "SccGetEvents-Funktion"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetEvents-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft ein Statusereignis in der Warteschlange ab.  
  
## Syntax  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 lpFileName  
 \[in, out\] Der Puffer, in dem das Quellcodeverwaltungs\-Plug\-in die zurückgegebenen Dateinamen \(bis zu Zeichen \_MAX\_PATH\) versetzt.  
  
 lpStatus  
 \[in, out\] Gibt den Statuscode zurück \(siehe [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md) Mögliche Werte\).  
  
 pnEventsRemaining  
 \[in, out\] Anzahl der Einträge in der Warteschlange verbleibt, nach dem Aufruf zurückgegeben. Wenn diese Zahl groß ist, kann der Aufrufer aufrufen, beschließen die [SccQueryInfo](../extensibility/sccqueryinfo-function.md) alle Informationen auf einmal zu erhalten.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Ruft Ereignisse erfolgreich war.|  
|SCC\_E\_OPNOTSUPPORTED|Diese Funktion wird nicht unterstützt.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Diese Funktion wird aufgerufen, während der Verarbeitung im Leerlauf, um festzustellen, ob Statusupdates für Dateien unter Versionskontrolle wurden. Das Quellcodeverwaltungs\-Plug\-in verwaltet Status aller Dateien, die er kennt, und wenn eine Änderung des Status finden Sie das Plug\-in, den Status und die zugehörige Datei in einer Warteschlange gespeichert werden. Wenn `SccGetEvents` aufgerufen wird, wird der obersten Element der Warteschlange abgerufen und zurückgegeben wird. Diese Funktion ist beschränkt auf nur zuvor zwischengespeicherten Informationen zurückgegeben werden sollen und benötigen eine sehr schnelle Verarbeitung \(also keine Lesen des Datenträgers oder Status Quellcode\-Verwaltungssystem zur\) Andernfalls kann die Leistung der IDE gestartet werden zu beeinträchtigen.  
  
 Wenn keine Aktualisierung des Clientstatus Bericht vorhanden ist, speichert das Quellcodeverwaltungs\-Plug\-in eine leere Zeichenfolge in den Puffer, der auf `lpFileName`. Andernfalls das plug\-in speichert den vollständigen Pfadnamen der Datei für die die Statusinformationen geändert hat, und den entsprechende Statuscode zurückgibt \(einer der Werte finden Sie unter [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md)\).  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Datei\-Statuscode](../extensibility/file-status-code-enumerator.md)