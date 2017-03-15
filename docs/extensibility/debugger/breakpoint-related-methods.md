---
title: "Haltepunkt-verwandten Methoden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Haltepunkt-Methoden"
  - "Haltepunkte, Methoden"
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Haltepunkt-verwandten Methoden
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Modul \(Debug\) muss DE die Einstellung von Haltepunkten unterstützen.  Visual Studio\-Debugunterstützung die folgenden Typen von Haltepunkten:  
  
-   Gebunden  
  
     Angefordert von der Benutzeroberfläche und an einem angegebenen Speicherort der Code erfolgreich gebunden  
  
-   Schwebend  
  
     Angefordert von der Benutzeroberfläche jedoch den tatsächlichen Anweisungen noch nicht gebundener  
  
## Erörterung  
 Ein anstehender Haltepunkt tritt beispielsweise auf, wenn die Anweisungen noch nicht geladen werden.  Wenn der Code geladen wird, versuchen auf Code ausstehender Haltepunkte am Speicherort vorgeschriebenen d. h. auf Einfügungs\-Unterbrechungs Anweisungen im Code zu binden.  Ereignisse werden dem Debuggen von Manager der Sitzung \(SDM\), um erfolgreichen Bindung anzugeben gesendet oder zu benachrichtigen, dass eine Bindung Fehler aufgetreten ist.  
  
 Ein anstehender Haltepunkt verwaltet auch eigene interne Liste der zugehörigen gebundenen Haltepunkte.  Ein anstehender Haltepunkt kann die Einfügung mehrerer Haltepunkte im Code verursachen.  Das Visual Studio debuggen, die Benutzeroberfläche zeigt eine Strukturansicht eines anstehenden Haltepunkten und ihre entsprechenden gebundenen Haltepunkte an.  
  
 Erstellung und Verwendung von anstehenden Haltepunkts erfordern die Implementierung der [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)\-Methode sowie der folgenden Methoden aus [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)\-Schnittstellen.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob ein angegebener anstehender Haltepunkt zu einem Speicherort des Codes gebunden werden kann.|  
|[Binden](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bindet einen angegebenen anstehenden Haltepunkt zu einem oder mehreren Code speicherorten.|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Zustand eines anstehenden Haltepunkts ab.|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft den Haltepunkt Anforderungen ab, die verwendet wird, um einen anstehenden Haltepunkt zu erstellen.|  
|[Aktivieren](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand eines anstehenden Haltepunkts.|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Haltepunkte aufgelistet, die von einem anstehenden Haltepunkt gebunden sind.|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler von Haltepunkten aufgelistet, die von einem anstehenden Haltepunkt auftreten.|  
|[Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht einen anstehenden Haltepunkt, und alle Haltepunkte, die aus ihm gebunden sind.|  
  
 Um die gebundenen Haltepunkte Haltepunkte und Fehler aufzulisten, müssen Sie alle Methoden aus [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) und [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)implementieren.  
  
 Ausstehende Haltepunkte, die an einem Speicherort des Codes binden, benötigen Implementierung der folgenden Methoden [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den anstehenden Haltepunkt ab, der einen Haltepunkt enthält.|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand eines gebundenen Haltepunkte ab.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die Auflösung von Haltepunkt ab, die den Haltepunkt beschreibt.|  
|[Aktivieren](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert einen Haltepunkt.|  
|[Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht einen gebundenen Haltepunkt.|  
  
 Auflösungs\- und Anforderungsinformationen erfordern Implementierung der folgenden Methoden [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) .  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Haltepunkts ab, der von einer Auflösung dargestellt wird.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft den Haltepunkt auflösungs Informationen ab, die den Haltepunkt beschreibt.|  
  
 Die Behebung der Fehler, die möglicherweise während der Bindung auftreten können, benötigt die Implementierung der folgenden Methoden [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den anstehenden Haltepunkt ab, der einen Fehler breakpoint enthält.|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die Auflösung von Fehlern Haltepunkt ab, die den Fehler beschreibt. breakpoint|  
  
 Die Behebung der Fehler, die möglicherweise während binden auftreten können, benötigt die folgenden Arten von [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ eines Haltepunkts ab.|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen Auflösungs eines Haltepunkts ab.|  
  
 Das Anzeigen des Quellcodes an einem Haltepunkt müssen Sie die Methoden von [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und\/oder die Methoden von [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)zu implementieren.  
  
## Siehe auch  
 [Steuerung der Ausführung und Status Bewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)