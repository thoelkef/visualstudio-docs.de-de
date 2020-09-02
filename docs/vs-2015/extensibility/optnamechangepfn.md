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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194105"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dies ist eine Rückruffunktion, die in einem aufzurufenden [sccsetoption](../extensibility/sccsetoption-function.md) -Operator (using-Option) angegeben wird `SCC_OPT_NAMECHANGEPFN` und zur Übermittlung von Namensänderungen verwendet wird, die vom Quellcodeverwaltungs-Plug-in an der IDE vorgenommen wurden.  
  
## <a name="signature"></a>Signatur  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 pvcallerdata  
 in Benutzer Wert, der in einem vorherigen [csetoption-aufrufswert](../extensibility/sccsetoption-function.md) (using-Option) angegeben wurde `SCC_OPT_USERDATA` .  
  
 pszoldname  
 in Der ursprüngliche Name der Datei.  
  
 psznewname  
 in Der Name, in den die Datei umbenannt wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn eine Datei während eines Quell Code Verwaltungs Vorgangs umbenannt wird, kann das Quellcodeverwaltungs-Plug-in die IDE über diesen Rückruf über die Namensänderung benachrichtigen.  
  
 Wenn die IDE diesen Rückruf nicht unterstützt, ruft Sie " [sccsetoption](../extensibility/sccsetoption-function.md) " nicht auf, um Sie anzugeben. Wenn das Plug-in diesen Rückruf nicht unterstützt, wird von der-Funktion zurückgegeben, `SCC_E_OPNOTSUPPORTED` `SccSetOption` Wenn die IDE versucht, den Rückruf festzulegen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von der IDE implementierte Rückruf Funktionen](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
