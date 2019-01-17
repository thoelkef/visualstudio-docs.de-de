---
title: IProvideExpressionContexts-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91f4251fec57001ba6c7a4ea1804ec72371418bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345096"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts-Schnittstelle
Bietet eine Möglichkeit zum Aufzählen von Ausdruckskontexten, die von einer bestimmten Komponente bekannt sind. Skript-Engines werden in der Regel diese Schnittstelle implementieren.  
  
 Prozessbasierten Debug-Manager verwendet diese Schnittstelle, um alle globalen ausdruckskontexten, die einem bestimmten Thread suchen.  
  
> [!NOTE]
>  Diese Schnittstelle wird von innerhalb des relevanten Threads aufgerufen werden. Es obliegt dem Implementierer, identifizieren den aktuellen Thread und einen entsprechenden Enumerator zurückgeben.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IProvideExpressionContexts` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Gibt einen Enumerator von ausdruckskontexten, die von dieser Komponente bezeichnet.|