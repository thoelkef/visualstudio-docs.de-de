---
title: Enumerationen (Visual Studio-Debugging) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80ad4db1090857d87e28d90d8478fbdea0905e86
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737138"
---
# <a name="enumerations-visual-studio-debugging"></a>Enumerations (Visual Studio Debugging)
Im Folgenden finden Sie [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Enumerationen für das Debugging SDK.

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) Gibt an, wie eine Prozess-ID in der [AD_PROCESS_ID-Struktur](../../../extensibility/debugger/reference/ad-process-id.md) interpretiert wird.

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) Gibt die Typen einer Adresse an.

- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) Gibt an, wo sich eine Baugruppe befindet.

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) Gibt den Grund für das Anfügen des Debugmoduls (DE) an einen Programmknoten an.

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) Gibt den Haltepunktbedingungsstil für ausstehende und gebundene Haltepunkte an.

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) Gibt den Fehlertyp eines Haltepunkts an.

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) Stellt optionale Flags bereit, die verwendet werden können, um zusätzliche Informationen beim Festlegen eines Haltepunkts anzugeben.

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md) Zählt gültige Werte für optionale Flags auf, die verwendet werden können, um zusätzliche Informationen anzugeben, wenn ein Haltepunkt festgelegt wird. Diese Enumeration erweitert [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) die BP_FLAGS-Enumeration.

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) Gibt den Positionstyp des Haltepunkts für eine Haltepunktanforderung an.

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) Gibt die Bedingung an, die der Anzahl der Haltepunktdurchlauferjahre zugeordnet ist, wodurch der Haltepunkt ausgelöst wird.

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) Gibt an, ob der Datenhaltepunkt emuliert oder in hardwareimplementiert wird.

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Gibt das Vorhandensein eines gebundenen Haltepunkts und an, ob er aktiviert ist.

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) Gibt an, ob sich der Haltepunkt an einem Codespeicherort befindet, ein Datenspeicherort oder ein anderer Haltepunkttyp ist.

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) Gibt den Grund an, warum ein Haltepunkt ungebunden war.

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) Gibt an, welche Informationen über eine fehlgeschlagene Auflösung eines Haltepunkts abgerufen werden sollen.

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Gibt an, welche Informationen zu einer Haltepunktanforderung abgerufen werden sollen.

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md) Zählt die gültigen Werte auf, die die Informationen angeben, die zu einer Haltepunktanforderung abgerufen werden sollen. Diese Enumeration erweitert [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) die BPREQI_FIELDS-Enumeration.

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) Gibt an, welche Informationen über die erfolgreiche Auflösung eines Haltepunkts abgerufen werden sollen.

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) Wird verwendet, um zu bestimmen, ob ein Programm die Ausführung beenden kann, nachdem es einen bestimmten Punkt in der Ausführung erreicht hat.

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) Ein Wert, der das Protokoll angibt, das für die Kommunikation zwischen einem Debugserver und dem Debugpaket verwendet wird.

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) Wählt verschiedene Arten von Konstruktoren aus.

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) Gibt die Kriterien für den Vergleich von zwei Speicherkontexten an.

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) Gibt an, welche Informationen zu einem Speicherkontext abgerufen werden sollen.

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) Beschreibt verschiedene Attribute für eine [IDebugProperty2-](../../../extensibility/debugger/reference/idebugproperty2.md) oder [IDebugReference2-Schnittstelle.](../../../extensibility/debugger/reference/idebugreference2.md)

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) Gibt an, warum der Prozess zum Debuggen gestartet wurde.

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) Gibt an, welche Informationen zu einem Debugeigenschaftenobjekt abgerufen werden sollen.

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) Gibt an, welche Informationen zu einem Debugreferenzobjekt abgerufen werden sollen.

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Gibt die Flags für die Demontage an.

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) Gibt an, welche Informationen zu einem Demontagefeld abgerufen werden sollen.

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) Gibt den Bereich des Demontagestreams an.

- [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) Zählt die gültigen Werte auf, die die Arten von Informationen darstellen, die von einem [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) entnommen und dem Benutzer angezeigt werden sollen.

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) Gibt die Kriterien für den Vergleich von zwei Dokumentkontexten an.

- [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) Gibt an, wie viel vom Status eines Programms abgeladen werden soll.

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) Gibt an, wie der Typ eines [IDebugField-Objekts](../../../extensibility/debugger/reference/idebugfield.md) interpretiert werden soll.

- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) Stellt die Gründe dar, warum Bearbeiten und Fortfahren nicht verfügbar ist.

- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) Gibt Flags an, die die Ausdruckauswertung steuern.

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md) Zählt die gültigen Werte für Flags auf, die die Ausdrucksauswertung steuern. Diese Enumeration erweitert die EVALFLAGS-Enumeration. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) Gibt die Ereignisattribute an.

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) Gibt den Ausnahmestatus an.

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Gibt an, welche Informationen zu einem [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) abgerufen werden sollen.

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) Gibt die Art des Felds an, das in einem [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) enthalten ist.

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) Zählt weitere Arten von Feldern auf, die ein [IDebugField-Objekt](../../../extensibility/debugger/reference/idebugfield.md) enthalten kann. Diese Enumeration erweitert [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) die FIELD_KIND-Enumeration.

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) Gibt Modifikatoren für einen Feldtyp an.

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Gibt die Informationen an, die über ein Stapelrahmenobjekt abgerufen werden sollen.

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) Gibt den Typ des Hostnamens an.

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) Gibt den Namenstyp der abzurufenden Dateien an.

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) Gibt an, welche Aktionen beim Abfangen von Ausnahmen ausgeführt werden sollen.

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) Gibt an, wie ein Programm gestartet werden soll.

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) Gibt an, welche Art von Informationen für einen bestimmten Computer abgerufen werden sollen.

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) Wird verwendet, um eine Maschine zu beschreiben.

- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) Gibt den Nachrichtentyp und den Grund an.

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) Wird verwendet, um ein Modul zu beschreiben.

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) Gibt die Flags für die Debugmodulinformationen an.

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Gibt den Status von Symbolen für ein Modul an.

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) Wählt die Falloption für übereinstimmende Namen aus.

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) Gibt den Typ eines Objekts aus dem Ausdrucksauswertungswert an.

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) Gibt an, wie ein Ausdruck analysiert wird.

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) Gibt den Status eines ausstehenden Haltepunkts an (ein Haltepunkt, der noch nicht gebunden wurde).

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) Gibt die ausstehenden Haltepunktstatusflags an.

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md) Definiert die Metadaten, die über einen Portlieferanten abgerufen werden können.

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Es wurde angegeben, welche Art von Informationen für einen Prozess abgerufen werden sollen.

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) Beschreibt oder gibt Eigenschaften eines Prozesses an.

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md) Zählt die gültigen Werte des Programms auf, die Flags zerstören.

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) Gibt Eigenschaften an, die einem Programmanbieter zugeordnet sind.

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) Gibt die gewünschten Eigenschaften an, die von einem Programmanbieter abgerufen werden sollen.

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) Gibt den Typ des Vergleichs für Referenzen an.

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) Gibt den Referenztyp an.

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) Gibt die Position an, von der aus mit der Suche in einer Demontage begonnen werden soll.

- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) Gibt die Schrittart für das Schrittschritten an.

- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) Gibt die Schritteinheit für das Schrittschritten an.

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) Gibt an, welche Art von Symbolinformationen abgerufen werden sollen.

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) Beschreibt die Attribute eines Dokuments.

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) Gibt an, welche Informationen zu einem Thread abgerufen werden sollen.

- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) Gibt den Status des Threads an.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h, sh.h oder ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
