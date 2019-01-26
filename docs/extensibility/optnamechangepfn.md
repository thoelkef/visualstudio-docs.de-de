---
title: OPTNAMECHANGEPFN | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31f46f8b392d5d3b37aed91a6867d80835be0d23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963917"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Dies ist eine Callback-Funktion angegeben, die in einem Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) (mithilfe der Option `SCC_OPT_NAMECHANGEPFN`) und wird verwendet, um die von vorgenommenen Namensänderungen das Quellcodeverwaltungs-Plug-in zurück zur IDE zu kommunizieren.  
  
## <a name="signature"></a>Signatur  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvCallerData  
 [in] Benutzerwert in einem vorherigen Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) (mithilfe der Option `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] Der ursprüngliche Name der Datei.  
  
 pszNewName  
 [in] Der Name der Datei wurde in umbenannt.  
  
## <a name="return-value"></a>Rückgabewert  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Datei während der einen Quellcodeverwaltungsvorgang umbenannt wird, kann das Quellcodeverwaltungs-Plug-in der IDE über die Änderung des über diesen Rückruf benachrichtigen.  
  
 Wenn dieser Rückruf in die IDE nicht unterstützt wird, ruft er nicht die [SccSetOption](../extensibility/sccsetoption-function.md) angegeben. Wenn das plug-in dieses Rückrufs nicht unterstützt, wird zurückgegeben, `SCC_E_OPNOTSUPPORTED` aus der `SccSetOption` funktionieren, wenn die IDE versucht wird, um den Rückruf festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)