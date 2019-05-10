---
title: IProcessDebugManager-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944789"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager-Schnittstelle
Die primäre Schnittstelle für den prozessbasierten Debug-Manager. Diese Schnittstelle kann eine virtuelle Anwendung aus einem Prozess erstellen, hinzufügen oder entfernen. Sie können die Stapelrahmen und Anwendungsthreads auflisten.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IProcessDebugManager` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Erstellt ein neues Objekt der Debug-Anwendung für diese Anwendung an.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Gibt ein Standardobjekt für die Anwendung für den aktuellen Prozess zurück.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Fügt eine Anwendung den computerbasierten Debug-Manager-Liste ausgeführter Anwendungen.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Entfernt eine Anwendung aus der ausgeführten Anwendungsliste.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Erstellt eine neue Debug-Dokument-Hilfe für diese Anwendung an.|