---
title: IDebugThreadCall-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726940"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall-Schnittstelle
Die `IDebugThreadCall` Schnittstelle wird von einer Komponente, die threadübergreifende Aufrufe mit stellt in der Regel implementiert die `IDebugThread` marshalling-Implementierung, die der Prozess-Manager (PDM).  
  
 Ruft die PDM die `IDebugThreadCall` -Schnittstelle in der gewünschten Thread und die `IDebugThreadCall` Schnittstelle leitet den Aufruf an die gewünschte Implementierung. Die `IDebugThreadCall` Schnittstelle wandelt die Parameterinformationen, die in den Parametern der entsprechenden nach oben übergeben.  
  
 Die `IDebugThreadCall` Schnittstelle ist eine Freethread-Objekt.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugThreadCall` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Aufrufe zum Ausführen von Code in einem anderen Thread verarbeitet.|