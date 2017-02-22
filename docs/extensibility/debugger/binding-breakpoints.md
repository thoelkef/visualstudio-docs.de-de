---
title: "Binden der Haltepunkte | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Haltepunkte, binden"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Binden der Haltepunkte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn die Benutzer legt einen Haltepunkt, etwa, indem sie die IDE, F9 drücken, dass die Debugsitzung und formuliert aufgefordert werden, den Haltepunkt zu erstellen.  
  
## Festlegen eines Haltepunktes  
 Festlegen eines Haltepunktes sind zwei Schritte, da der Code oder die Daten, die in den Haltepunkt betroffen sind, möglicherweise noch nicht verfügbar sind.  Zuerst muss der Haltepunkt und anschließend beschrieben werden, während Code oder Daten verfügbar ist, muss er für diesen Code oder an Daten gebunden sind wie folgt:  
  
1.  Der Haltepunkt wird von den relevanten Module Debuggen DES \(\) angefordert, und dann wird der Haltepunkt in den Code oder an Daten gebunden, während er verfügbar ist.  
  
2.  Der Haltepunkt wird die Anforderung an die Debugsitzung gesendet, die sie für alle relevanten DES sendet.  Jedes DE beschließt, der den Haltepunkt zu behandeln, erstellt einen entsprechenden anstehenden Haltepunkt.  
  
3.  Die Debugsitzung sammelt die ausstehenden Haltepunkte und sendet sie zurück zum Debuggen von der Komponente Paket \(Visual Studio\).  
  
4.  Das Debuggen von Paket erfordert die Debugsitzung auf den ausstehenden Haltepunkt in den Code oder an Daten gebunden wird.  Die Debugsitzung sendet diese Anforderung für alle relevanten DES.  
  
5.  Wenn DE in der Lage ist, den Haltepunkt zu binden, sendet er ein gebundenes Ereignis des Haltepunkts an die Debugsitzung.  Wenn dies nicht der Fall ist, sendet er ein Haltepunkt fehlerereignis.  
  
## Ausstehende Haltepunkte  
 Ein anstehender Haltepunkt kann auf mehrere Code speicherorten binden.  Beispielsweise kann eine Zeile des Quellcodes für Vorlage zu jeder Code in C\-Format C\+\+\-Compiler Zeichenfolge binden, die von der Vorlage generiert wird.  Die Debugsitzung kann ein gebundenes Ereignis des Haltepunkts verwenden, um die Code kontexte aufzulisten, die an einem Haltepunkt gebunden sind, zu dem Zeitpunkt, als das Ereignis aufgetreten sind.  Mehr Code kontexte können später gebunden werden. Daher sendet möglicherweise DE gebundenen Ereignisse des mehrere Haltepunkte für jede Anforderung von Bindungen.  Es darf nur ein Haltepunkt DE fehlerereignis Bindungen pro Anforderung senden.  
  
## Implementierung  
 Programmgesteuert wird das Debuggen in der Sitzung Paket Debuggen Manager \(SDM\) und weist dieser eine [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)\-Schnittstelle, die eine [BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md) Struktur, die den festzulegenden Haltepunkt beschreibt.  Obwohl Haltepunkte aus mehreren Formularen sein können, lösen sie letztendlich zu einem Code oder einen Datenkontext auf.  
  
 Das SDM führt diesen Aufruf von allen relevanten DE, indem Sie seine [CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)\-Methode aufruft.  Wenn DE beschließt, um den Haltepunkt zu behandeln, erstellt er eine [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)\-Schnittstelle und gibt diese zurück.  Das SDM ruft diese Schnittstellen und übergibt sie an den Debug\- als einzelne Paket `IDebugPendingBreakpoint2`\-Schnittstelle.  
  
 Bisher sind keine Ereignisse generiert wurde.  
  
 Das Paket versucht anschließend, die den ausstehenden Haltepunkt in den Code oder die Daten binden, indem [Binden](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)aufrufen, der von DE implementiert wird.  
  
 Wenn der Haltepunkt gebunden ist, sendet [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)\-Ereignisschnittstelle um eine DE Debuggen auf Paket.  Das Debuggen von Paket verwendet diese Schnittstelle, um alle Code kontexte \(oder den einzelnen Datenkontext,\) aufzulisten, die dem Haltepunkt gebunden werden, indem [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)aufruft, das eine oder mehrere [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)\-Schnittstellen zurückgibt.  Die [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)\-Schnittstelle gibt eine [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)\-Schnittstelle zurück, und [GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) gibt eine [BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) Gesamtmenge zurück, die den Code oder den Datenkontext enthält.  
  
 Wenn DE nicht in der Lage ist, den Haltepunkt zu binden, sendet er eine einzelne [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)\-Ereignisschnittstelle zum Debuggen von Paket.  Das Debuggen von Paket ruft den Fehlertyp \(Fehler oder Warnung\) und Informationsmeldung ab, indem [GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)aufruft, gefolgt von [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) und [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md).  Dadurch wird eine [BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur zurück, die den Fehlertyp und die Nachricht enthält.  
  
 Wenn DE behandelt, einen Haltepunkt jedoch nicht gebunden werden kann, wird ein Fehler vom Typ `BPET_TYPE_ERROR`zurück.  Das Debuggen von Paket reagiert, indem ein Fehlerdialogfeld angezeigt werden, und die IDE fügt ein Ausrufs Haltepunkt innerhalb des Symbols für das Symbol auf der linken Seite der Quellcodezeile.  
  
 Wenn DE einen Haltepunkt behandelt, kann es nicht gebunden werden, aber ein anderes DE bände kann es, eine Warnung zurückgibt.  Die IDE reagiert, indem ein Fragen Haltepunkt innerhalb des Symbols für das Symbol auf der linken Seite der Quellcodezeile platziert.  
  
## Siehe auch  
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)