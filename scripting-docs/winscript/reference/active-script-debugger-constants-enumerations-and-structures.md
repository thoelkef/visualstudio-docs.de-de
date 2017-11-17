---
title: Active Script-Debugger-Konstanten, Enumerationen und Strukturen | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bd41fe91fdf030b957d800248343198f2617018
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Konstanten, Enumerationen und Strukturen für Active Script-Debugger
Die folgenden Konstanten, Enumerationen und Strukturen werden von den Active Debugging-Schnittstellen verwendet.  
  
## <a name="constants-enumerations-and-structures"></a>Konstanten, Enumerationen und Strukturen  
  
|Konstanten|Beschreibung|  
|---------------|-----------------|  
|[APPBREAKFLAGS-Konstanten](../../winscript/reference/appbreakflags-enumeration.md)|Geben den aktuellen Debugzustand für Anwendungen und Threads an.|  
|[DEBUG_TEXT-Konstanten](../../winscript/reference/debug-text-constants.md)|Flags, die während der Option [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[TEXT_DOC_ATTR-Konstanten](../../winscript/reference/text-doc-attr-constants.md)|Beschreiben die Attribute des Dokuments.|  
  
|Enumerationen|Beschreibung|  
|------------------|-----------------|  
|[APPBREAKFLAGS-Konstanten](../../winscript/reference/appbreakflags-enumeration.md)|Geben den aktuellen Debugzustand für Anwendungen und Threads an.|  
|[APPLICATION_NODE_EVENT_FILTER-Enumeration](../../winscript/reference/application-node-event-filter-enumeration.md)|Geben die mit einem Filter auszuschließenden Knoten an.|  
|[BREAKPOINT_STATE-Enumeration](../../winscript/reference/breakpoint-state-enumeration.md)|Gibt den Zustand eines Haltepunkts an.|  
|[BREAKREASON-Enumeration](../../winscript/reference/breakreason-enumeration.md)|Gibt an, was die Unterbrechung verursacht hat.|  
|[BREAKRESUMEACTION-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)|Beschreibt, wie der Vorgang von einem Haltepunkt aus fortgesetzt wird.|  
|[DOCUMENTNAMETYPE-Enumeration](../../winscript/reference/documentnametype-enumeration.md)|Beschreibt, welche Typen für ein Dokument abzurufen sind.|  
|[ERRORRESUMEACTION-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)|Beschreibt, wie der Vorgang von einem Laufzeitfehler aus fortgesetzt wird.|  
|[JS_PROPERTY_ATTRIBUTES-Enumeration](../../winscript/reference/js-property-attributes-enumeration.md)|Zeigt die Attribute einer Eigenschaft an.|  
|[JS_PROPERTY_MEMBERS-Enumeration](../../winscript/reference/js-property-members-enumeration.md)|Flags, um den Typ der Informationen anzugeben, die in einer Anforderung für Member eines Objekts zurückzugeben sind.|  
|[JsDebugReadMemoryFlags-Enumeration](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Flags um Verhalten anzugeben, wenn Arbeitsspeicher gelesen werden.|  
|[SCRIPT_DEBUGGER_OPTIONS-Enumeration](../../winscript/reference/script-debugger-options-enumeration.md)|Gibt einen Satz von Optionen oder Funktionen an, die für den angefügten Debugger gelten.|  
|[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND-Enumeration](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Gibt die Art der ausgelösten Ausnahme an.|  
|[SOURCE_TEXT_ATTR-Konstanten](../../winscript/reference/source-text-attr-enumeration.md)|Beschreiben die Attribute eines einzelnen Zeichens des Quelltexts.|  
  
|Strukturen|Beschreibung|  
|----------------|-----------------|  
|[DebugStackFrameDescriptor-Struktur](../../winscript/reference/debugstackframedescriptor-structure.md)|Listet Stapelrahmen auf und fügt die Ausgabe mehrerer Enumeratoren in demselben Thread zusammen.|  
|[JS_NATIVE_FRAME-Struktur](../../winscript/reference/js-native-frame-structure.md)|Stellt einen Stapelrahmen dar.|  
|[JsDebugPropertyInfo-Struktur](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Gibt Informationen über eine Eigenschaft an.|  
|[TEXT_DOCUMENT_ARRAY-Struktur](../../winscript/reference/text-document-array-structure.md)|Stellt einen Satz Dokumente bereit.|