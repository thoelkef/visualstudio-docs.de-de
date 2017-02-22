---
title: "SccQueryChanges-Funktion | Microsoft Docs"
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
  - "SccQueryChanges"
helpviewer_keywords: 
  - "SccQueryChanges-Funktion"
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccQueryChanges-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion listet bestimmte Dateien, die Informationen über Namensänderungen für jede Datei über eine Callback\-Funktion bereitgestellt.  
  
## Syntax  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Der Source Control\-Plug\-in Kontextzeiger.  
  
 nFiles  
 \[in\] Anzahl der Dateien in `lpFileNames` Array.  
  
 lpFileNames  
 \[in\] Array von Dateinamen für die Informationen abgerufen.  
  
 pfnCallback  
 \[in\] Rückruffunktion für jede Datei in der Liste \(siehe [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Details\).  
  
 pvCallerData  
 \[in\] Wert, der unverändert an die Rückruffunktion übergeben wird.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Der Abfrageprozess erfolgreich abgeschlossen.|  
|SCC\_E\_PROJNOTOPEN|Das Projekt wurde nicht im Datenquellen\-Steuerelement geöffnet.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte.|  
|SCC\_E\_NONSPECIFICERROR|Nicht angegeben oder allgemeine Fehler.|  
  
## Hinweise  
 Änderungen, die abgefragt wird, die auf den Namespace sind: insbesondere umbenennen, hinzufügen und Entfernen einer Datei.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Fehlercodes](../extensibility/error-codes.md)