---
title: IDebugThreadCall-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149522"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall-Schnittstelle
Die `IDebugThreadCall` Schnittstelle wird von einer Komponente, die threadübergreifende Aufrufe mit stellt in der Regel implementiert die `IDebugThread` marshalling-Implementierung von prozessbasierten Debug-Manager (PDM).  
  
 Der PDM Ruft die `IDebugThreadCall` -Schnittstelle in den gewünschten Thread und die `IDebugThreadCall` Schnittstelle sendet den Aufruf an die gewünschte Implementierung. Die `IDebugThreadCall` Schnittstelle wandelt die Parameterinformationen, die entsprechende oben in den Parametern übergeben.  
  
 Die `IDebugThreadCall` Schnittstelle ist ein Freethread-Objekt.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugThreadCall` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Verarbeitet die Aufrufe an Code in einem anderen Thread auszuführen.|