---
title: IActiveScriptErrorDebug110-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72f545f5a48fc7b8aa3f9250b13a62ba659e94bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436059"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110-Schnittstelle
Funktionell die [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md). Diese Schnittstelle wird durch die JavaScript-Engine implementiert, um zu bestimmen, warum ein BREAKREASON_ERROR-Ereignis aufgetreten ist.  
  
> [!IMPORTANT]
> Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IActiveScriptErrorDebug110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Gibt die Ausnahmeart für eine ausgelöste Ausnahme zurück.|