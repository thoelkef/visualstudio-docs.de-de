---
title: BP_LOCATION_CODE_FILE_LINE | Microsoft-Dokumentation
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
- BP_LOCATION_CODE_FILE_LINE
helpviewer_keywords:
- BP_LOCATION_CODE_FILE_LINE structure
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce292de7bfbc5f1ebabffdc17ec478d4d3592e75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521705"
---
# <a name="bplocationcodefileline"></a>BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BP_LOCATION_CODE_FILE_LINE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-location-code-file-line).  
  
Enthält die Daten für den Speicherort eines Haltepunkts an einer bestimmten Zeile in einer Code-Quelldatei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## <a name="members"></a>Member  
 `bstrContext`  
 Der Kontext des Haltepunkts, in der Regel eine Methode oder Funktion Namen wie für eine Aufrufliste.  
  
 `pDocPos`  
 Die [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) -Objekt, die Dokumentposition des Haltepunkts darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

