---
title: IDispError-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idisperror-interface"></a>IDispError-Schnittstelle
Stellt ausführliche Informationen zu kontextbezogenen bereit.  
  
> [!NOTE]
>  Diese Schnittstelle ist nicht implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDispError` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Ruft eine bestimmte Art von Fehlerinformationen ab.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Ruft den nächsten `IDispError` Objekt.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Ruft den Fehlercode aus der `IDispError` Objekt.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Gibt den sprachabhängig programmgesteuerten Bezeichner für die Klasse oder eine Anwendung, die den Fehler ausgelöst.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Gibt den Pfad der Hilfedatei und des Themas, die den Fehler, wenn möglich wird erläutert, die Kontext-ID zurück.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Gibt eine Beschreibung des Fehlers zurück.|