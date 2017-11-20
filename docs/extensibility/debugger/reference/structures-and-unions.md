---
title: Strukturen und Unions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2fc3225bda24a9ea0d759c1f684801723ea396f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="structures-and-unions"></a>Strukturen und Unions
Im folgenden sind Strukturen und Unions in Visual Studio Debugging-SDK.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Gibt die Prozess-ID, die ein System-ID oder eine GUID an.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Beschreibt die Bedingungen, unter denen ein Breakpoint ausgelöst werden.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Beschreibt die Auflösung eines Haltepunkts auf Fehler, einschließlich Speicherort, Programm- und Threads an.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Gibt den Typ der Struktur verwendet, um die Position des Haltepunkts zu beschreiben.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Definiert die Komponenten, die die Position eines Haltepunkts an einer Adresse im Code beschreiben.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Beschreibt den Speicherort eines Haltepunkts, die direkt an eine Adresse im zu debuggenden Programms gebunden ist.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Beschreibt die Position eines Haltepunkts in Zeile in einer Code-Quelldatei an.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Beschreibt die Offsetposition eines Haltepunkts in einer Funktion im Code.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Verwendet zum Festlegen von codehaltepunkte auf Grundlage einer Zeichenfolge, die der Benutzer aus der IDE eingeben können.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Verwendet zum Festlegen von datenbreakpoints, die auf eine Zeichenfolge, die der Benutzer aus der IDE eingeben können.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Beschreibt die Auflösung eines Haltepunkts an einer bestimmten Stelle.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Beschreibt die Anzahl und die Bedingungen, auf denen ein Breakpoint ausgelöst wird, nach dem zuvor übergeben.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Enthält die Informationen erforderlich, um einen Haltepunkt zu implementieren.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Enthält die erforderlichen Informationen an einen Haltepunkt zu implementieren (identisch mit der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur enthält jedoch die GUID, Einschränkung und Ablaufverfolgungspunkt Lieferanteninformationen).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Beschreibt den Speicherort eines Haltepunkts Code.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Beschreibt das Ergebnis der Bindung eines Haltepunkts an.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Beschreibt die gebundenen Haltepunktinformationen für einen codehaltepunkt oder eines Haltepunkts.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Gibt die Struktur der Position des Haltepunkts Auflösung an.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Ein Array von Zeichenfolgen beschreibt.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Gibt Informationen über einen Feldtyp Metadaten entnommen.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Beschreibt einen Aufruf einer Funktion oder Methode an.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Beschreibt den Computer, auf dem der Debugger ausgeführt wird.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Beschreibt eine Liste von GUIDs.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Beschreibt eine Arbeitsspeicher-Kontext oder Codekontext.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Beschreibt eine Adresse in einem Programm, das gerade gedebuggt wird.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Stellt eine Reihe von verschiedenen Arten von Adressen.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Einen benutzerdefinierten Viewer identifiziert, oder geben Sie die Schnellansicht.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Beschreibt eine Debugeigenschaft, die wiederum ein Objekt von einer hierarchischen Struktur beschreibt, die Namen, Typ und Wert verfügt.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Beschreibt einen Verweis.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Beschreibt die Disassemblierung der IDE für die Anzeige.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Beschreibt eine Ausnahme oder ein Laufzeitfehler ausgelöst, die für das Programm, das gerade gedebuggt wird.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Einer lokalen Variablen, Parameter oder andere Feld beschreiben.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Beschreibt einen Stapelrahmen entspricht.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Ein Array von eindeutigen Bezeichnern für verfügbare Debugmodule beschreibt.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Verwendet die JustMyCode-Informationen für ein Modul festgelegt.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Beschreibt einen bestimmten Computer an.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Beschreibt ein Arrayelement in einem Array an.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Beschreibt die Adresse eines Felds einer Klasse oder Struktur an.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Beschreibt die Adresse einer lokalen Variablen in einem Bereich (in der Regel eine Funktion oder Methode).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Beschreibt die Adresse einer Methode einer Klasse.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Beschreibt einen Parameter einer Methode oder Funktion.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Beschreibt einen Rückgabewert einer Methode oder Funktion.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Beschreibt einen Feldtyp Metadaten entnommen.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Beschreibt ein bestimmtes Modul (DLL, EXE-Datei oder Assembly) an.  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Beschreibt die Statusinformationen zur Symbolsuchpfaden, die durchsucht wurden.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Beschreibt eine systemeigene Adresse an.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Beschreibt einen Feldtyp stammt aus einer PDB-Symbol.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Beschreibt den Status eines Haltepunkts, das zum Binden an einen Speicherort bereit ist.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Beschreibt einen Prozess an.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Beschreibt eine Liste der [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Objekte, die Programm-Knoten darstellen.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Beschreibt die Prozesse, die auf einem Computer ausgeführt.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Beschreibt den Zeilen- und Spaltennummer Speicherort im angegebenen Text.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Beschreibt die Eigenschaften eines Threads.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Ein Feld beschreibt.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Beschreibt eine physische Adresse an.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Beschreibt eine Adresse, relativ zum wird, eine `this` Zeiger (`Me` in Visual Basic).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h, sh.h oder ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)