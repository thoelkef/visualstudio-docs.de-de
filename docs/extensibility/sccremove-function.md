---
title: "SccRemove-Funktion | Microsoft Docs"
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
  - "SccRemove"
helpviewer_keywords: 
  - "SccRemove-Funktion"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRemove-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion löscht Dateien aus dem Quellcode\-Verwaltungssystem.  
  
## Syntax  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
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
 \[in\] Array von Namen voll gekennzeichneter lokaler Pfad Dateien entfernt werden soll.  
  
 lpComment  
 \[in\] Der Kommentar auf jede entfernte Datei angewendet werden.  
  
 Bestanden  
 \[in\] Befehl Flags \(nicht verwendeten\).  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Deinstallation war erfolgreich.|  
|SCC\_E\_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht in einem Quellcodeverwaltungsprojekt.|  
|SCC\_E\_OPNOTSUPPORTED|Dieser Vorgang wird von Quellcode\-Verwaltungssystem nicht unterstützt.|  
|SCC\_E\_ISCHECKEDOUT|Eine Datei kann nicht entfernt werden, da ein Benutzer derzeit ausgecheckt hat.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_NONSPECIFICERROR|Unspezifischen Ausfall. Datei wurde nicht entfernt.|  
|SCC\_I\_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
  
## Hinweise  
 Diese Funktion entfernt die Dateien aus dem Quellcode\-Verwaltungssystem, jedoch nicht von der Festplatte des Benutzers gelöscht.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)