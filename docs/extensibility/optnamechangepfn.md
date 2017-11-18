---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OPTNAMECHANGEPFN
helpviewer_keywords: OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 666174c4f0f54679907bd239a81c5c369dc09a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Dies ist eine Rückruffunktion, die in einem Aufruf angegebenen der [SccSetOption](../extensibility/sccsetoption-function.md) (mithilfe der Option `SCC_OPT_NAMECHANGEPFN`) und wird verwendet, um vorgenommene Namensänderungen durch die quellcodeverwaltung-Plug-in zurück auf die IDE zu kommunizieren.  
  
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
 [in] Der Name der Datei wurde umbenannt in.  
  
## <a name="return-value"></a>Rückgabewert  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Datei während einer Quelle-Steuerungsvorgang umbenannt wird, kann das Quellsteuerelement-Plug-in der IDE über die Änderung über diesen Rückruf benachrichtigen.  
  
 Wenn dieser Rückruf in die IDE nicht unterstützt wird, rufen sie nicht die [SccSetOption](../extensibility/sccsetoption-function.md) anzugeben. Wenn das plug-in dieses Rückrufs nicht unterstützt, gibt es zurück `SCC_E_OPNOTSUPPORTED` aus der `SccSetOption` -Funktion, wenn die IDE versucht, den Rückruf zu setzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Rückruffunktionen implementiert, die von der IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)