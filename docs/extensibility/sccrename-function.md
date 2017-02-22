---
title: "SccRename-Funktion | Microsoft Docs"
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
  - "SccRename"
helpviewer_keywords: 
  - "SccRename-Funktion"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccRename-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion benennt eine Datei im Quellcode\-Verwaltungssystem.  
  
## Syntax  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpFileName  
 \[in\] Der vollqualifizierte Name der umbenannten Datei.  
  
 lpNewName  
 \[in\] Der vollqualifizierte Name für neuen. Wenn der Verzeichnispfad unterschiedlich ist, wurde die Datei aus einem Unterverzeichnis auf einen anderen verschoben.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Der Umbenennungsvorgang erfolgreich abgeschlossen wurde.|  
|SCC\_E\_PROJNOTOPEN|Das Projekt ist nicht in der quellcodeverwaltung geöffnet.|  
|SCC\_E\_FILENOTCONTROLLED|Diese Datei befindet sich nicht in Datenquellen\-Steuerelement.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang abzuschließen.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Das Projekt konnte nicht als Teil der Umbenennung erstellt werden.|  
|SCC\_E\_OPNOTPERFORMED|Der Vorgang wurde nicht ausgeführt.|  
|SCC\_E\_NONSPECIFICERROR|Nicht angegeben oder allgemeine Fehler.|  
  
## Hinweise  
 Diese Funktion kann verwendet werden, um eine Datei umbenennen oder Verschieben von einem Speicherort im Quellcode\-Verwaltungssystem. Das Datenquellen\-Steuerelement, das plug\-in sollten nicht versuchen, Zugriff auf die Datei auf dem Datenträger. Es obliegt der IDE auf die lokale Datei umbenennen.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)