---
title: IDebugProperty3 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 479827cc83486d6bb9c68d0749b8870cd6c41861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694760"
---
# <a name="idebugproperty3"></a>IDebugProperty3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle bietet Unterstützung für:  
  
- Abrufen einer willkürlich langen Zeichenfolge, die der-Eigenschaft zugeordnet ist.  
  
- Zuordnen einer eindeutigen ID zur-Eigenschaft.  
  
- Abrufen einer Liste benutzerdefinierter Viewer für die-Eigenschaft.  
  
- Festlegen des Werts einer Eigenschaft mit der Möglichkeit, resultierende Fehler zu melden  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle für das gleiche Objekt, das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) implementiert, um Unterstützung für lange Zeichen folgen, Eigenschaften-IDs und benutzerdefinierte Viewer bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für eine `IDebugProperty2` Schnittstelle auf, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Zusätzlich zu den von geerbten Methoden macht `IDebugProperty2` die- `IDebugProperty3` Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Gibt die Länge der Zeichenfolge zurück, die der-Eigenschaft zugeordnet ist.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Gibt die Zeichenfolge in einem vom Benutzer bereitgestellten Puffer zurück.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Erstellt eine eindeutige ID für diese Eigenschaft.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Zerstört die eindeutige ID für diese Eigenschaft.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Gibt die Anzahl der benutzerdefinierten Viewer zurück, mit der diese Eigenschaft angezeigt werden kann.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Gibt die Liste der benutzerdefinierten Viewer zurück, mit der diese Eigenschaft angezeigt werden kann.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Legt den Wert dieser Eigenschaft fest und gibt eine Fehlermeldung zurück, wenn etwas schief gegangen ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 [Setvalueasstringwitherror](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) ist die bevorzugte Methode für den Sitzungs-Debug-Manager (SDM), den Wert einer Eigenschaft festzulegen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
