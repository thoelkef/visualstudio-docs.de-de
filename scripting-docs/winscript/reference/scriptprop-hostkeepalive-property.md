---
title: SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a39ae7100c5567d2b03b7998077b20b1078810aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734140"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft
Dient zum angeben, und zwar unabhängig davon, ob das Skriptmodul bleiben sollten voll funktionsfähig, wenn ausstehende Verweise vorhanden sind.  
  
 Verwendung [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) zum Festlegen dieser Eigenschaft `true`. Wenn diese Eigenschaft, um festgelegt wird `true`, das Skriptmodul bleiben voll funktionsfähig, solange es mindestens einen ausstehenden Verweis auf das Skriptmodul sich selbst oder gibt ein `IDispatch` Zeiger auf ein JavaScript-Objekt, das erstellt wird, über die Skripterstellung Modul. Wenn diese Eigenschaft festgelegt wird, um `true`, sollten nicht explizit geschlossen oder das Skriptmodul zurücksetzen, indem die [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) oder [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) Methoden. Die Version von den letzten Verweis auf ein Skriptobjekt fährt das Skriptmodul.  
  
## <a name="syntax"></a>Syntax  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Anforderungen  
 Diese Eigenschaft wird nur in der Version von activscp.idl, die mit dem installierten [!INCLUDE[win8](../../javascript/includes/win8-md.md)], mit KB 2707082 für Internet Explorer 8 auf [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], oder mit KB 2722913 für Internet Explorer 9 auf [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] oder [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].