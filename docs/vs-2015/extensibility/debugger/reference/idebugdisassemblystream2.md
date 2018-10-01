---
title: IDebugDisassemblyStream2 | Microsoft-Dokumentation
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
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f72cea28e47bdd14681c1f843a2620a43162885
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522999"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugDisassemblyStream2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdisassemblystream2).  
  
Diese Schnittstelle stellt einen Stream von Anweisungen dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugmodul implementiert diese Schnittstelle, um die Disassembly des Programms Code zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf der [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) Methodenrückgabe diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugDisassemblyStream2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Liest die Anleitung beginnend mit der aktuellen Position im Stream Disassembly.|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Verschiebt des lesezeigers im Disassemblyfenster Stream einer bestimmten Anzahl von Anweisungen, die relativ zur angegebenen Position.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Gibt einen Code-Speicherort-Bezeichner für einen bestimmten Code-Kontext zurück.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Gibt ein für eine angegebene Standortbezeichner Code Context-Objekt zurück.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Gibt einen Code geographical Location Identifier, die den aktuellen Speicherort darstellt.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ruft das Quelldokument, dem dieser Stream Disassembly zugeordnet ist.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ruft den Bereich dieses Disassembly-Streams ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ruft die Größe dieses Streams Disassembly.|  
  
## <a name="remarks"></a>Hinweise  
 Im gesamten Adressraum oder nur eine Funktion oder dieses Moduls innerhalb des Bereichs darstellt, kann der Disassembly-Stream erstellt werden. Jede Anweisung wird dargestellt, indem eine [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) durch einen Aufruf zurückgegebene Struktur der [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

