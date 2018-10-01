---
title: IDebugContainerField | Microsoft-Dokumentation
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
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a911fe64f397a3a671787db00877a07f5ed1ccaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513645"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugContainerField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcontainerfield).  
  
Diese Schnittstelle stellt ein Symbol oder ein Typ, der ein Container für andere Symbole oder Typen ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein symbolanbieter implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle. Diese Schnittstelle ist auch die Basisklasse für alle Schnittstellen, die Container darstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Viele Methoden für viele Schnittstellen zurückgeben dieser Schnittstelle. Da es sich um eine Basisklasse für alle Container handelt, spezialisiertere Schnittstellen erhalten Sie von dieser Schnittstelle mit [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Diese Schnittstellen umfassen [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), und [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den Methoden für die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Schnittstelle, die diese Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Erstellt einen Enumerator für die Felder des Containers.|  
  
## <a name="remarks"></a>Hinweise  
 Arrays (Container für Variablen), (Container für Methoden und Variablen)-Klassen und Methoden (der Container für Parameter und lokalen Variablen) sind Beispiele für Container.  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Symbolanbieterschnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

