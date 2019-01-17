---
title: IDebugSessionProvider-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345148"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider-Schnittstelle
Die primäre Schnittstelle bereitgestellt, die von einem Debugger-IDE, um den Host und der Sprache ermöglichen initiiert Debuggen. Er richtet eine Debugsitzung für eine ausgeführte Anwendung. Diese Schnittstelle wird von computerbasierten Debug-Manager implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSessionProvider` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Startet eine Debugsitzung mit der angegebenen Anwendung.|