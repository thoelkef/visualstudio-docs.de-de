---
title: "SccProperties-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "SccProperties-Funktion"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccProperties-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion zeigt die Eigenschaften der quellcodeverwaltung für eine Datei oder ein Projekt.  
  
## Syntax  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpFileName  
 \[in\] Der Name der vollqualifizierte Pfad der Datei oder des Projekts.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Eigenschaften wurden erfolgreich angezeigt.|  
|SCC\_I\_RELOADFILE|Das Versionskontrollsystem wurde die Dateieigenschaften geändert, damit die IDE diese Datei neu geladen werden soll.|  
|SCC\_E\_PROJNOTOPEN|Das angegebene Projekt wurde nicht im Datenquellen\-Steuerelement geöffnet.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, können Sie die Eigenschaften dieser Datei oder eines Projekts anzeigen.|  
|SCC\_E\_FILENOTCONTROLLED|Die angegebene Datei oder das Projekt ist nicht in einem Quellcodeverwaltungsprojekt.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Unbekannte oder allgemeiner Fehler.|  
  
## Hinweise  
 Das Quellcodeverwaltungs\-Plug\-in zeigt die Eigenschaften in ein eigenes Dialogfeld.  
  
 Die Eigenschaften werden durch das Quellcodeverwaltungs\-Plug\-in definiert und unterscheidet sich möglicherweise von Plug\-in\-Plug\-in. Wenn das plug\-in den Benutzer ermöglicht das Ändern der Eigenschaften der quellcodeverwaltung einer Datei, sollte es zurückgeben `SCC_I_RELOAD` IDE signalisiert, die diese Datei oder das Projekt neu geladen werden muss.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)