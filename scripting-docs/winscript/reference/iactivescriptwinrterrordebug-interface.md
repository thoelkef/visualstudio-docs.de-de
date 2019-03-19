---
title: IActiveScriptWinRTErrorDebug-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60fbe5efe55b5347eb54eb4d6c010b6ab5903905
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144237"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug-Schnittstelle
Implementiert, die von der JavaScript-Engine zu erweiterten Windows-Runtime-Fehlerinformationen von einem [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md) Ereignis. Erreichen Sie eine QueryInterface rufen sie über eine [IActiveScriptError](../../winscript/reference/iactivescripterror.md) Objekt.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IActiveScriptWinRTErrorDebug`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Gibt die SID-Funktion für den Windows-Runtime-Fehler zurück, sofern verfügbar.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Gibt die Windows-Runtime eingeschränkt Verweiszeichenfolge Fehler, falls verfügbar.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Gibt die Windows-Runtime eingeschränkt fehlermeldungs-Zeichenfolge, falls verfügbar.|