---
title: IEnumDebugModules2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f66587f462e1bbfb60704c5c75dc2299cb9ce36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160974"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle zählt eine Liste von Modulen auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) implementiert diese Schnittstelle, um eine Liste von Modulen darzustellen, die für ein Programm geladen werden.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Visual Studio ruft [enummodule](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) auf, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugModules2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[Nächste](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Ruft eine angegebene Anzahl von Modulen in einer enumerationssequenz ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Überspringt eine angegebene Anzahl von Modulen in einer enumerationssequenz.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ruft die Anzahl der Module ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Visual Studio verwendet diese Schnittstelle hauptsächlich, um das Fenster **Module** zu aktualisieren.  
  
 Zum Zwecke des Debuggens in Visual Studio ist ein Programm eine logische Sequenz von Code Anweisungen, die Modul Grenzen überschreiten können. Daher ist eine Liste von Modulen für eine einzelne [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) -Schnittstelle erforderlich. Das erste Modul in der Liste enthält normalerweise den ersten Einstiegspunkt für das zugehörige Programm.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
