---
title: IDebugCustomAttribute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4230f8db75841e0ae7d990c906fe68cf71af701a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796908"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein benutzerdefiniertes Attribut, und er kann den Namen, übergeordneten und Klassentyp des Attributs bereitstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein symbolanbieter implementiert diese Schnittstelle, um benutzerdefinierte Attribute, die ein Symbol zugeordnet zu unterstützen. Es ist in der Regel für sein eigenes Objekt implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [Weiter](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) dieser Schnittstelle zurück. Ein Aufruf der [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) Methode gibt die [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugCustomAttribute`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Ruft das Feld, das an dem das aktuelle Attribut angefügt ist.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Ruft ab, der Typ des benutzerdefinierten Attributs-Klasse.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Ruft den Namen des benutzerdefinierten Attributs.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Ruft die Attributinformationen, wie ein Blob von Bytes ab.|  
  
## <a name="remarks"></a>Hinweise  
 Ein benutzerdefiniertes Attribut ist eine Struktur für c#, die benutzerdefinierten Metadaten zugeordnet, eine bestimmte Klasse oder Methode bereitstellt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

