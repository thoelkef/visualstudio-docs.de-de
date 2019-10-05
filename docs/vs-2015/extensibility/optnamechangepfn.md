---
title: OPTNAMECHANGEPFN | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194105"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dies ist eine Callback-Funktion angegeben, die in einem Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) (mithilfe der Option `SCC_OPT_NAMECHANGEPFN`) und wird verwendet, um die von vorgenommenen Namensänderungen das Quellcodeverwaltungs-Plug-in zurück zur IDE zu kommunizieren.  
  
## <a name="signature"></a>Signatur  
  
```cpp#  
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
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Datei während der einen Quellcodeverwaltungsvorgang umbenannt wird, kann das Quellcodeverwaltungs-Plug-in der IDE über die Änderung des über diesen Rückruf benachrichtigen.  
  
 Wenn dieser Rückruf in die IDE nicht unterstützt wird, ruft er nicht die [SccSetOption](../extensibility/sccsetoption-function.md) angegeben. Wenn das plug-in dieses Rückrufs nicht unterstützt, wird zurückgegeben, `SCC_E_OPNOTSUPPORTED` aus der `SccSetOption` funktionieren, wenn die IDE versucht wird, um den Rückruf festzulegen.  
  
## <a name="see-also"></a>Siehe auch  
 [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
