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
ms.openlocfilehash: 2c67ff6e458f8350ef36a8a454e017b3ce6ea114
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144926"
---
# <a name="idisperror-interface"></a>IDispError-Schnittstelle
Stellt ausführliche kontextbedingte Fehlerinformationen bereit.  
  
> [!NOTE]
>  Diese Schnittstelle ist nicht implementiert.  
  
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