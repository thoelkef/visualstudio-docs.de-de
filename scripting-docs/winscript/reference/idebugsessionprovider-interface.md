---
title: IDebugSessionProvider-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fe73901d92cb42675ff9ec981bd9b90dcca5d546
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148986"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider-Schnittstelle
Die primäre Schnittstelle bereitgestellt, die von einem Debugger-IDE, um den Host und der Sprache ermöglichen initiiert Debuggen. Er richtet eine Debugsitzung für eine ausgeführte Anwendung. Diese Schnittstelle wird von computerbasierten Debug-Manager implementiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugSessionProvider` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Startet eine Debugsitzung mit der angegebenen Anwendung.|