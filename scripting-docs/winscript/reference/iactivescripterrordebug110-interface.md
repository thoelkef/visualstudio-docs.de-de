---
title: IActiveScriptErrorDebug110-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 152f12154acc59b88fc8b1c9a176ac87a5da847d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110-Schnittstelle
Fügt Funktionen für die [IActiveScriptDebug-Schnittstelle](../../winscript/reference/iactivescriptdebug-interface.md). Diese Schnittstelle wird durch das JavaScript-Modul implementiert, um zu bestimmen, warum ein BREAKREASON_ERROR-Ereignis aufgetreten ist.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IActiveScriptErrorDebug110`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Gibt die Ausnahmeart für eine ausgelöste Ausnahme zurück.|