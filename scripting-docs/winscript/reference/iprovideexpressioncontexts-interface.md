---
title: IProvideExpressionContexts-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728100"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts-Schnittstelle
Bietet eine Möglichkeit zum Aufzählen von ausdruckskontexten, die von einer bestimmten Komponente bezeichnet. Script-Module in der Regel implementieren Sie diese Schnittstelle.  
  
 Der Prozess-Manager verwendet diese Schnittstelle, um alle globalen ausdruckskontexten, die ein bestimmter Thread zugeordnet zu suchen.  
  
> [!NOTE]
>  Diese Schnittstelle wird von innerhalb des relevanten Threads aufgerufen. Es wird vom Implementierer identifizieren den aktuellen Thread und einen entsprechenden Enumerator zurück.  
  
## <a name="methods"></a>Methoden  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IProvideExpressionContexts` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Gibt einen Enumerator von ausdruckskontexten, die von dieser Komponente bezeichnet.|