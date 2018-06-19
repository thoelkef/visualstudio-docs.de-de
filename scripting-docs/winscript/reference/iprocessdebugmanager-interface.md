---
title: IProcessDebugManager-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729220"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager-Schnittstelle
Primäre Schnittstelle auf der Debug-Prozess-Manager. Diese Schnittstelle kann erstellen, hinzufügen oder entfernen eine virtuelle Anwendung aus einem Prozess. Sie können Stapelrahmen und Anwendungsthreads aufgelistet werden.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IProcessDebugManager` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Erstellt ein neues Objekt der Debug-Anwendung für diese Anwendung an.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Gibt ein Standardobjekt für die Anwendung für den aktuellen Prozess zurück.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Fügt eine Anwendung auf den Computer Debug-Manager-Liste ausgeführter Anwendungen.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Entfernt eine Anwendung aus der Ausführung Anwendungsliste.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Erstellt ein neues Debug-Dokument-Hilfsprogramm für diese Anwendung an.|