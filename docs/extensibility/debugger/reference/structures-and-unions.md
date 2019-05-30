---
title: Strukturen und Unions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2da39e0327f9a0be2cf0f61227de5ea51af03285
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329117"
---
# <a name="structures-and-unions"></a>Structures and Unions
Im folgenden sind Strukturen und Unions in Visual Studio Debugging SDK.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) gibt an, die Prozess-ID, die möglicherweise eine System-ID oder eine GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) beschreibt die Bedingungen, unter denen ein Haltepunkt wird ausgelöst.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) beschreibt die Auflösung der ein Haltepunkt Fehler einschließlich Ort, Programm und Threads.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) gibt den Typ der Struktur verwendet, um den Speicherort des Haltepunkts zu beschreiben.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) definiert die Komponenten, die die Position eines Haltepunkts an einer Adresse im Code zu beschreiben.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) beschreibt den Speicherort eines Haltepunkts an, die direkt an eine Adresse in das Programm im Debugmodus befindlichen gebunden ist.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) den Speicherort der einen Haltepunkt in Zeile in einer Codedatei für die Quelle beschreibt.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) wird beschrieben, die Offsetposition der eines Haltepunkts in einer Funktion im Code.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) verwendet zum Festlegen von Code Breakpoints, die basierend auf eine Zeichenfolge, die der Benutzer aus der IDE eingeben kann.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) zum Festlegen von Datenhaltepunkten, die auf eine Zeichenfolge basieren, die der Benutzer aus der IDE eingeben können.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) beschreibt die Auflösung der einen Haltepunkt an einer bestimmten Position.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) wird beschrieben, die Anzahl und die Bedingungen aus, auf dem ein Haltepunkt ausgelöst wird, nachdem zuvor übergeben.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) enthält die Informationen erforderlich, um einen Haltepunkt zu implementieren.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) enthält die Informationen erforderlich, um einen Haltepunkt zu implementieren (identisch mit der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur enthält jedoch Informationen zu Anbieter-GUID, Einschränkung und Ablaufverfolgungspunkt).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) beschreibt den Speicherort eines Haltepunkts Code.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) beschreibt das Ergebnis der Bindung eines Haltepunkts für Daten.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) beschreibt die gebundene Haltepunkt-Informationen für einen codehaltepunkt oder eines Haltepunkts für Daten.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) gibt an, die Struktur der die Position des Haltepunkts Auflösung.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) wird beschrieben, ein Array von Zeichenfolgen.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) gibt Informationen über einen Feldtyp aus Metadaten erstellt.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) einen Aufruf einer Funktion oder Methode beschreibt.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) wird beschrieben, den Computer, auf dem der Debugger ausgeführt wird.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) wird beschrieben, eine Liste von GUIDs.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) beschreibt ein Speicherkontext oder Codekontext.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) eine Adresse in einem Programm im Debugmodus befindlichen beschreibt.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) stellt eine Anzahl verschiedener Arten von Adressen.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) identifiziert einen benutzerdefinierten Viewer oder typschnellansicht.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) beschreibt eine Debugeigenschaft, die wiederum ein Objekt von einer hierarchischen Wesens beschreibt, das über Name, Typ und Wert verfügt.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) beschreibt einen Verweis.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) Disassembly für die IDE für die Anzeige beschreibt.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) Ausnahme oder zur Laufzeit Fehler wird ausgelöst, durch das derzeit debuggte Programm beschreibt.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) beschreibt eine lokale Variable, Parameter oder anderen Feldern.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) beschreibt einen Stapelrahmen.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) wird beschrieben, ein Array von eindeutigen Bezeichnern für verfügbare Debug-Engines.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) verwendet, um die JustMyCode-Informationen für ein Modul festzulegen.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) wird beschrieben, einen bestimmten Computer.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) ein Arrayelement in einem Array beschreibt.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) die Adresse eines Felds, einer Klasse oder Struktur beschreibt.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) beschreibt die Adresse einer lokalen Variablen in einem Gültigkeitsbereich (in der Regel eine Funktion oder Methode).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) die Adresse einer Methode einer Klasse beschreibt.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) beschreibt einen Parameter einer Methode oder Funktion.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) Rückgabewert für eine Methode oder Funktion beschreibt.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) beschreibt einen Feldtyp aus Metadaten erstellt.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) beschreibt ein bestimmtes Modul (DLL, EXE-Datei oder Assembly).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) beschreibt Statusinformationen über die Symbolsuchpfade, die durchsucht wurden.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) eine native Adresse beschreibt.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) beschreibt den Typ eines Felds, ein Symbol für die PDB-Datei entnommen.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) beschreibt den Status eines Haltepunkts an, die an einen Speicherort gebunden werden kann.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) beschreibt einen Prozess.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) beschreibt eine Liste der [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) programmknoten darstellende – Objekte.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) beschreibt Prozesse, die auf einem Computer ausgeführt.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) beschreibt den Zeilen- und Spaltennummer Speicherort im angegebenen Text.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) beschreibt die Eigenschaften eines Threads.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) Typ des Felds beschreibt.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) eine physische Adresse beschreibt.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) wird beschrieben, eine Adresse, die relativ zu einem `this` Zeiger (`Me` in Visual Basic).

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h sh.h oder ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)