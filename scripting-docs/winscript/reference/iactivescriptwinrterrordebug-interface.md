---
title: IActiveScriptWinRTErrorDebug-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34fcc4f1dc3ebc21f9303ba49f1709f2d023a29a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug-Schnittstelle
Durch das JavaScript-Modul, um erweiterte Fehlerinformationen für Windows-Runtime von bereitzustellen implementiert eine [BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md) Ereignis. Sie erreichen eine QueryInterface zum Abrufen von einer [IActiveScriptError](../../winscript/reference/iactivescripterror.md) Objekt.  
  
> [!IMPORTANT]
>  Diese Schnittstelle wird von PDM v11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="methods"></a>Methoden  
 Die `IActiveScriptWinRTErrorDebug`-Schnittstelle macht die folgenden Methoden verfügbar:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Gibt die Funktion SID für den Windows-Runtime-Fehler zurück, sofern verfügbar.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Gibt die Windows-Runtime eingeschränkt Verweis Fehlerzeichenfolge, falls verfügbar.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Gibt die Windows-Runtime-Fehlerzeichenfolge eingeschränkt, falls verfügbar.|