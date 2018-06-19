---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1598ec8a6e5fca5275384c00433d74d22ce3505
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107893"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Diese Schnittstelle stellt einen Datenstrom von Anweisungen dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Ein Debugmodul implementiert diese Schnittstelle, um die Disassembly von einem Programm-Codes zu unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf der [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) Methodenrückgabe diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugDisassemblyStream2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Liest die Anweisungen, die von der aktuellen Position im Disassemblyfenster Datenstrom ab.|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Verschiebt den schreibgeschützten Zeiger im Disassembly-Datenstrom einer bestimmten Anzahl von Anweisungen relativ zu einer angegebenen Position.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Gibt die ID für den Standort einen Code für einen bestimmten Code-Kontext zurück.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Gibt ein Kontextobjekt für Code, eine ID für den Standort angegebenen Code entspricht.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Gibt einen Code Position-Bezeichner, der die aktuelle Codeposition darstellt.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ruft das Quelldokument, dem dieser Stream Disassembly zugeordnet ist.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ruft den Bereich dieses Streams Disassembly ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ruft die Größe dieses Streams Disassembly ab.|  
  
## <a name="remarks"></a>Hinweise  
 Die Disassembly Stream kann erstellt werden, im gesamten Adressraum oder nur eine Funktion oder dem Modul innerhalb des Bereichs darstellt. Jede Anweisung wird dargestellt, indem eine [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur zurückgegeben, die durch einen Aufruf der [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)