---
title: "SccDirQueryInfo-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "SccDirQueryInfo-Funktion"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccDirQueryInfo-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion überprüft eine Liste der vollqualifizierten Verzeichnisse für den aktuellen Status.  
  
## Syntax  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 nDirs  
 \[in\] Die Anzahl der Verzeichnisse, die abgefragt werden ausgewählt.  
  
 lpDirNames  
 \[in\] Ein Array von vollständig qualifizierten Pfads, der abgefragt werden soll.  
  
 lpStatus  
 \[in, out\] Eine Arraystruktur für das Quellcodeverwaltungs\-Plug\-in, um die Statusflags zurückzugeben \(siehe [Directory\-Statuscode](../extensibility/directory-status-code-enumerator.md) Details\).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Abfrage war erfolgreich.|  
|SCC\_E\_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem unterstützt diesen Vorgang nicht.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Die Funktion füllt das return Array mit einer Bitmaske der Bits aus der `SCC_DIRSTATUS` Familie \(finden Sie unter [Directory\-Statuscode](../extensibility/directory-status-code-enumerator.md)\), einen Eintrag für jedes Verzeichnis angegeben. Das Statusarray, die vom Aufrufer zugeordnet ist.  
  
 Die IDE verwendet diese Funktion auf, bevor ein Verzeichnis umbenannt wird, um zu überprüfen, ob das Verzeichnis Quellcodeverwaltungsprojekt Abfragen, ob es einen entsprechenden Projekt verfügt. Wenn das Verzeichnis nicht verwaltet ist, kann die IDE die richtige Warnung für dem Benutzer bereitstellen.  
  
> [!NOTE]
>  Wenn ein Quellcodeverwaltungs\-Plug\-in entscheidet, eine oder mehrere der Statuswerte nicht implementiert, sollte nicht implementierte Bits 0 \(null\) festgelegt werden.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Directory\-Statuscode](../extensibility/directory-status-code-enumerator.md)