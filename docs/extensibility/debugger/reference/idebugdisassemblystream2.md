---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2-Schnittstelle"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Datenstrom von Anweisungen dar.  
  
## Syntax  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Debuggen Modul implementiert diese Schnittstelle, um die Disassembly des Codes eines Programms zu unterstützen.  
  
## Hinweise für Aufrufer  
 Ein Aufruf der [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)\-Methode gibt diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugDisassemblyStream2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Liest die Anweisungen, die von der aktuellen Position im Disassemblys datenstrom.|  
|[Suchen](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Verschiebt den Zeiger im Disassemblys lesen datenstrom eine festgelegte Anzahl von Anweisungen im Verhältnis zu einer angegebenen Position.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Gibt einen Speicherort des Codes Bezeichner für einen bestimmten Code Elementkontext zurück.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Gibt ein Code für die gemäß einem angegebenen Speicherort des Codes Bezeichner zurück.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Gibt einen Speicherort des Codes Bezeichner zurück, der den aktuellen Speicherort des Codes darstellt.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ruft das Quelldokument ab, das diesem Disassemblys datenstrom zugeordnet ist.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ruft den Bereich dieses Disassemblysdatenstroms ab.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ruft die Größe dieses Disassemblysdatenstroms ab.|  
  
## Hinweise  
 Der Disassemblys datenstrom kann erstellt werden, um den gesamten Adressraum oder nur eine Funktion oder ein Modul innerhalb des Leerraums darzustellen.  Jede Anweisung wird von einer [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Struktur dargestellt, die durch einen Aufruf der [Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)\-Methode zurückgegeben wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)