---
title: IDispError-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85704ed9e9a9493ef02e4d4d68a84a2d1623533f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446861"
---
# <a name="idisperror-interface"></a>IDispError-Schnittstelle
Stellt ausführliche kontextbedingte Fehlerinformationen bereit.  
  
> [!NOTE]
> Diese Schnittstelle ist nicht implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDispError` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Ruft einen bestimmten Typ von Fehlerinformationen ab.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Ruft die nächste `IDispError` Objekt.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Ruft den Fehlercode aus der `IDispError` Objekt.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Gibt den sprachabhängige programmgesteuerten Bezeichner für die Klasse oder eine Anwendung, die den Fehler ausgelöst hat.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Gibt den Pfad der Hilfedatei und des Themas, das den Fehler, wenn möglich wird erläutert, die Kontext-ID zurück.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Gibt eine textbeschreibung des Fehlers zurück.|