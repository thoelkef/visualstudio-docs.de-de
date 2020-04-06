---
title: Strukturen und Gewerkschaften | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713494"
---
# <a name="structures-and-unions"></a>Structures and Unions
Im Folgenden finden Sie Strukturen und Unions im Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) Gibt die Prozess-ID an, bei der es sich entweder um eine System-ID oder eine GUID handelt.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Beschreibt die Bedingungen, unter denen ein Haltepunkt ausgelöst wird.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Beschreibt die Auflösung eines Fehlerhaltepunkts, einschließlich Speicherort, Programm und Thread.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Gibt den Strukturtyp an, der zum Beschreiben der Position des Haltepunkts verwendet wird.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) Definiert die Komponenten, die den Speicherort eines Haltepunkts an einer Adresse im Code beschreiben.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) Beschreibt den Speicherort eines Haltepunkts, der direkt an eine Adresse in dem zu debuggenden Programm gebunden ist.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Beschreibt den Speicherort eines Haltepunkts in der Zeile in einer Codequelldatei.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Beschreibt die Versatzposition eines Haltepunkts an einer Funktion im Code.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) Wird zum Festlegen von Codehaltepunkten basierend auf einer Zeichenfolge verwendet, die der Benutzer über die IDE eingeben kann.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) Wird zum Festlegen von Datenhaltepunkten verwendet, die auf einer Zeichenfolge basieren, die der Benutzer aus der IDE eingeben kann.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) Beschreibt die Auflösung eines Haltepunkts an einer bestimmten Position.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Beschreibt die Anzahl und die Bedingungen, unter denen ein Haltepunkt ausgelöst wird, nachdem er zuvor übergeben wurde.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Enthält die Informationen, die zum Implementieren eines Haltepunkts erforderlich sind.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Enthält die Informationen, die zum Implementieren eines Haltepunkts erforderlich sind (wie die [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur, enthält jedoch Die Hersteller-GUID, Einschränkung senkstelle und Ablaufverfolgungspunktinformationen).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) Beschreibt den Speicherort eines Code-Breakpoints.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) Beschreibt das Ergebnis der Bindung eines Datenhaltepunkts.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Beschreibt die gebundenen Haltepunktinformationen für einen Code-Breakpoint oder einen Datenhaltepunkt.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Gibt die Struktur der Position der Haltepunktauflösung an.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Beschreibt ein Array von Zeichenfolgen.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) Gibt Informationen zu einem Feldtyp an, der aus Metadaten entnommen wurde.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) Beschreibt einen Aufruf einer Funktion oder Methode.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) Beschreibt den Computer, auf dem der Debugger ausgeführt wird.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) Beschreibt eine Liste von GUIDs.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Beschreibt einen Speicherkontext oder Codekontext.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) Beschreibt eine Adresse in einem Zufeinerprogramm, das gedebugpft wird.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Stellt eine von mehreren verschiedenen Arten von Adressen dar.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Identifiziert einen benutzerdefinierten Viewer oder eine Typvisualisierung.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Beschreibt eine Debugeigenschaft, die wiederum ein Objekt hierarchischer Natur mit Name, Typ und Wert beschreibt.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) Beschreibt einen Verweis.

- [DemontageDaten](../../../extensibility/debugger/reference/disassemblydata.md) Beschreibt die Demontage zur Anzeige auf der IDE.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Beschreibt einen Ausnahme- oder Laufzeitfehler, der vom zu debuggenden Programm ausgelöst wird.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Beschreibt eine lokale Variable, einen Parameter oder ein anderes Feld.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Beschreibt einen Stapelrahmen.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) Beschreibt ein Array eindeutiger Bezeichner für verfügbare Debugmodule.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) Wird verwendet, um die JustMyCode-Informationen für ein Modul festzulegen.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) Beschreibt einen bestimmten Computer.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) Beschreibt ein Arrayelement innerhalb eines Arrays.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) Beschreibt die Adresse eines Felds einer Klasse oder Struktur.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) Beschreibt die Adresse einer lokalen Variablen innerhalb eines Bereichs (in der Regel eine Funktion oder Methode).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) Beschreibt die Adresse einer Methode einer Klasse.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) Beschreibt einen Parameter einer Methode oder Funktion.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Beschreibt einen Rückgabewert aus einer Methode oder Funktion.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) Beschreibt einen Feldtyp, der aus Metadaten entnommen wurde.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) Beschreibt ein bestimmtes Modul (DLL, EXE oder Assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Beschreibt Statusinformationen zu Symbolsuchpfaden, die durchsucht wurden.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) Beschreibt eine systemeigene Adresse.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) Beschreibt einen Feldtyp, der aus einem PDB-Symbol entnommen wurde.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) Beschreibt den Status eines Haltepunkts, der an einen Codespeicherort gebunden werden kann.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) Beschreibt einen Prozess.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) Beschreibt eine Liste von [IDebugProgramNode2-Objekten,](../../../extensibility/debugger/reference/idebugprogramnode2.md) die Programmknoten darstellen.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) Beschreibt Prozesse, die auf einem Computer ausgeführt werden.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) Beschreibt die Zeilen- und Spaltenposition im angegebenen Text.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) Beschreibt die Eigenschaften eines Threads.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Beschreibt den Typ eines Felds.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) Beschreibt eine physische Adresse.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) Beschreibt eine Adresse, die `this` relativ`Me` zu einem Zeiger (in Visual Basic) ist.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h, sh.h oder ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
