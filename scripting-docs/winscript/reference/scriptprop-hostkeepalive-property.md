---
title: SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724bfcb1ec42617cda4c89269cb0160accafb1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840334"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft
Dient zum angeben, und zwar unabhängig davon, ob die Skript-Engine aufbewahrt werden sollen voll funktionsfähig, wenn ausstehende Verweise vorhanden sind.  
  
 Verwendung [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) zum Festlegen dieser Eigenschaft auf `true`. Wenn diese Eigenschaft, um festgelegt wird `true`, die Skript-Engine bleibt voll funktionsfähig, solange es ist mindestens eine ausstehende Verweise auf die Skript-Engine selbst oder auf eine `IDispatch` Zeiger auf ein JavaScript-Objekt, das erstellt wird, über die Skripterstellung -Engine. Wenn diese Eigenschaft auf festgelegt ist `true`, sollten Sie nicht explizit geschlossen oder Zurücksetzen die Skript-Engine mithilfe der [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) oder [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) Methoden. Die Version von der letzte Verweis auf ein Skriptobjekt fährt die Skript-Engine.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Anforderungen  
 Diese Eigenschaft wird nur in der Version von activscp.idl, die mit dem installierten [!INCLUDE[win8](../../javascript/includes/win8-md.md)], mit KB 2707082 für Internet Explorer 8 auf [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], oder mit KB 2722913 für Internet Explorer 9 auf [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] oder [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].