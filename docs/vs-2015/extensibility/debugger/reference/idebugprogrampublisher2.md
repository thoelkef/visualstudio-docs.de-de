---
title: IDebugProgramPublisher2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d49173a4c1f10be1544cf07b0b01640321d6d181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697295"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht einem Debugmodul (de) oder benutzerdefinierten Port Zulieferern das Registrieren von Programmen für das Debuggen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um Programme zu registrieren, die gedebuggt werden, damit Sie für das Debuggen über mehrere Prozesse sichtbar sind.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie die com- `CoCreateInstance` Funktion mit `CLSID_ProgramPublisher` auf, um diese Schnittstelle zu erhalten (siehe Beispiel). Ein oder ein benutzerdefinierter Port Lieferant verwendet diese Schnittstelle, um Programmknoten zu registrieren, die Programme darstellen, die gedebuggt werden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in der Vtable-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Macht einen Programmknoten für den und den Sitzungs-Debug-Manager (SDM) verfügbar.|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Entfernt einen Programmknoten, sodass er nicht mehr verfügbar ist.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Stellt ein Programm für den und den SDM zur Verfügung.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Entfernt ein Programm, sodass es nicht mehr verfügbar ist.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Legt ein Flag fest, das angibt, dass ein Debugger vorhanden ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle macht Programme und Programmknoten verfügbar (d. h., veröffentlicht sie) für die Verwendung durch des und den Sitzungs-Debug-Manager (SDM). Um auf veröffentlichte Programme und Programmknoten zuzugreifen, verwenden Sie die [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) -Schnittstelle. Dies ist die einzige Möglichkeit, wie Visual Studio erkennen kann, dass ein Programm gedeppt wird.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie der Programm Verleger instanziiert und ein Programmknoten registriert wird. Dies wird aus dem Tutorial zum [Veröffentlichen des Programm Knotens](https://msdn.microsoft.com/d0100e02-4e2b-4e72-9e90-f7bc11777bae)entnommen.  
  
```cpp#  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
