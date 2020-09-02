---
title: IDebugStackFrame2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae9cad7102fb9a82deb43b2c8820ef52e77deeed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547002"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen einzelnen Stapel Rahmen in einer-Rückruf Stapel in einem bestimmten Thread dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle, um einen Stapel Rahmen darzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [enumframeinfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um eine [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Schnittstelle abzurufen. Rufen Sie [weiter](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) auf, um eine [frameInfo](../../../extensibility/debugger/reference/frameinfo.md) -Struktur abzurufen, die die `IDebugStackFrame2` Schnittstelle enthält.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugStackFrame2` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Code Kontext für diesen Stapel Rahmen ab.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokument Kontext für diesen Stapel Rahmen ab.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ruft den Namen des Stapel Rahmens ab.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ruft eine Beschreibung des Stapel Rahmens ab.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ruft eine Computer abhängige Darstellung des Bereichs physischer Adressen ab, der einem Stapel Rahmen zugeordnet ist.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ruft einen Auswertungs Kontext zum Durchsuchen der Ausdrucks Auswertung innerhalb des aktuellen Kontexts eines Stapel Rahmens und Threads ab.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ruft die Sprache ab, die einem Stapel Rahmen zugeordnet ist.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ruft eine Beschreibung der einem Stapel Rahmen zugeordneten Eigenschaften ab.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Erstellt einen Enumerator für Stapel Rahmen Eigenschaften.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ruft den Thread ab, der einem Stapel Rahmen zugeordnet ist.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird nur abgerufen, wenn das gedestete Programm an einem Haltepunkt angehalten wurde (entweder durch einen Benutzer Satz-Haltepunkt oder eine Ausnahme verursacht). Über diese Schnittstelle kann ein Ausdrucks Kontext zum Auswerten von Ausdrücken abgerufen werden, eine Liste der Register kann zurückgegeben werden, oder die Aufrufliste kann abgerufen und überprüft werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
