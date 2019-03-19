---
title: IMachineDebugManagerEvents-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcfcc2aed0fedefdc149b83e911d33cd3b54cdef
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153122"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents-Schnittstelle
Signaländerungen in der ausgeführten Anwendungsliste, die vom computerbasierten Debug-Manager verwaltet werden. Diese Schnittstelle kann durch den Debugger-IDE verwendet werden, um eine dynamische Liste der Anwendungen anzuzeigen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IMachineDebugManagerEvents` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Behandelt das Ereignis, wenn die Ausführung eine Anwendung hinzugefügt wird Liste der Anwendungen.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Behandelt das Ereignis, wenn eine Anwendung, aus der ausgeführten entfernt wird Anwendungsliste.|