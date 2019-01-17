---
title: IProcessDebugManager-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: 5feb67b1a616eeaa855b27cb12ea9b3146545ebd
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345122"
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