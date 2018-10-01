---
title: OPTNAMECHANGEPFN | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f729e00805fa1c73fe1e64197788dd31f2a2a41d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509091"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [OPTNAMECHANGEPFN](https://docs.microsoft.com/visualstudio/extensibility/optnamechangepfn).  
  
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

