---
title: "SccUninitialize-Funktion | Microsoft Docs"
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
  - "SccUninitialize"
helpviewer_keywords: 
  - "SccUninitialize-Funktion"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccUninitialize-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion löscht alle Zuweisungen oder geöffneten Verbindungen, die durch einen vorherigen Aufruf von erstellt die [SccInitialize](../extensibility/sccinitialize-function.md) als Vorbereitung für das Quellcodeverwaltungs\-Plug\-in heruntergefahren.  
  
## Syntax  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Der Zeiger auf die Datenquellen\-Steuerelement\-Plug\-in Context\-Struktur erstellt, der [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Bereinigung wurde erfolgreich abgeschlossen.|  
  
## Hinweise  
 Das Quellcodeverwaltungs\-Plug\-in ist verantwortlich für heruntergefahren werden, Vorbereiten und Freigeben von Arbeitsspeicher, der das plug\-in für Context\-Struktur zugewiesen wurde. Die Funktion wird einmal für jede Instanz eines Plug\-Ins aufgerufen. Ein Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md) dieser Aufruf vorausgeht. Keine Projekte können weiterhin geöffnet sein zum Zeitpunkt des Aufrufs von `SccUninitialize`.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)