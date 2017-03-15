---
title: "SccUncheckout-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUncheckout"
helpviewer_keywords: 
  - "SccUncheckout-Funktion"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUncheckout-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion wird eine vorherige Auschecken, wiederherstellen und den Inhalt der ausgewählten Datei oder Dateien in den Zustand vor dem Auschecken rückgängig gemacht. Alle Änderungen, die in die Datei seit dem Auschecken gehen verloren.  
  
## Syntax  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 \[in\] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 \[in\] Array der Namen von voll gekennzeichneter lokaler Pfad der Dateien für das Auschecken rückgängig gemacht.  
  
 Bestanden  
 \[in\] Befehl Flags \(nicht verwendet\).  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|"Auschecken rückgängig" war erfolgreich.|  
|SCC\_E\_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht vom Quellcode gesteuert.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler. Rückgängig: Auschecken nicht erfolgreich war.|  
|SCC\_E\_NOTCHECKEDOUT|Der Benutzer besitzt nicht die Datei ausgecheckt haben.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_PROJNOTOPEN|Das Projekt wurde nicht vom Datenquellen\-Steuerelement geöffnet.|  
|SCC\_I\_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
  
## Hinweise  
 Nach diesem Vorgang die `SCC_STATUS_CHECKEDOUT` und `SCC_STATUS_MODIFIED` Flags werden sowohl für die Dateien auf dem das Auschecken rückgängig ausgeführt wurde gelöscht werden.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)