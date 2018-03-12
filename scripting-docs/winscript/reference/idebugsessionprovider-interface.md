---
title: IDebugSessionProvider-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider-Schnittstelle
Die primäre Schnittstelle bereitgestellt, die von einem Debugger IDE zum Aktivieren von Host- und Sprache initiiert Debuggen. Dabei wird eine Debugsitzung für eine ausgeführte Anwendung. Diese Schnittstelle wird von der Computer-Manager implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSessionProvider` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Startet eine Debugsitzung mit der angegebenen Anwendung an.|