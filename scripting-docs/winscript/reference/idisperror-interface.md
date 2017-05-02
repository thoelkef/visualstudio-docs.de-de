---
title: "IDispError-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError-Schnittstelle"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError-Schnittstelle
Enthält ausführliche Fehlerinformationen kontextbedingte aufgeführt.  
  
> [!NOTE]
>  Diese Schnittstelle wird nicht implementiert.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDispError`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Ruft Fehlertypinformationen bestimmten ab.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Ruft das folgende `IDispError`\-Objekt ab.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Ruft den Fehlercode vom `IDispError`\-Objekt ab.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Gibt den sprachabhängigen Programmbezeichner für die Klasse oder die Anwendung zurück, die den Fehler ausgelöst hat.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Gibt den Pfad der Hilfedatei und der Kontexts\-ID des Themas zurück, das den Fehler erläutert, wenn möglich.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Gibt eine Textbeschreibung des Fehlers zurück.|