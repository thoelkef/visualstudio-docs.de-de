---
title: Strukturen und Unions | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f882eae12e700fe86ab747cc7ffbe3b5744298af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204847"
---
# <a name="structures-and-unions"></a>Structures and Unions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Im folgenden sind Strukturen und Unions in Visual Studio Debugging SDK.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Gibt die Prozess-ID, die möglicherweise eine System-ID oder eine GUID an.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Beschreibt die Bedingungen, unter denen ein Haltepunkt ausgelöst wird.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Beschreibt die Auflösung von einem Fehler Haltepunkt, einschließlich der Standort, Anwendung und Thread an.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Gibt den Typ der Struktur verwendet, um den Speicherort des Haltepunkts zu beschreiben.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Definiert die Komponenten, die die Position eines Haltepunkts an einer Adresse im Code zu beschreiben.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Beschreibt den Speicherort eines Haltepunkts an, die direkt an eine Adresse in das Programm im Debugmodus befindlichen gebunden ist.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Beschreibt den Speicherort eines Haltepunkts in Zeile in einer Code-Quelldatei.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Beschreibt die Offsetposition der eines Haltepunkts in einer Funktion im Code.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Verwendet zum Festlegen von Code Breakpoints, die basierend auf eine Zeichenfolge, die der Benutzer aus der IDE eingeben kann.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Verwendet zum Festlegen von datenbreakpoints, die auf eine Zeichenfolge basieren, die der Benutzer aus der IDE eingeben können.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Beschreibt die Auflösung eines Haltepunkts an einer bestimmten Position.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Beschreibt die Anzahl und die Bedingungen, von denen ein Haltepunkt ausgelöst wird, nach dem zuvor übergeben.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Enthält die Informationen erforderlich, um einen Haltepunkt zu implementieren.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Enthält die Informationen erforderlich, um einen Haltepunkt zu implementieren (identisch mit der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur enthält jedoch Informationen zu Anbieter-GUID, Einschränkung und Ablaufverfolgungspunkt).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Beschreibt den Speicherort eines Haltepunkts Code.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Beschreibt das Ergebnis der Bindung eines Haltepunkts für Daten.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Beschreibt die gebundene Haltepunkt-Informationen für einen codehaltepunkt oder eines Haltepunkts für Daten.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Gibt die Struktur der Haltepunktposition Auflösung.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Beschreibt ein Array von Zeichenfolgen.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Gibt Informationen über einen Feldtyp aus Metadaten erstellt.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Beschreibt einen Aufruf einer Funktion oder Methode an.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Beschreibt, den Computer, auf dem der Debugger ausgeführt wird.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Beschreibt eine Liste von GUIDs.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Beschreibt einen Speicherkontext oder Codekontext.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Beschreibt eine Adresse in einem Programm im Debugmodus befindlichen.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Stellt eine Anzahl verschiedener Arten von Adressen.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Einen benutzerdefinierten Viewer identifiziert, oder geben Sie die Schnellansicht.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Beschreibt eine Debugeigenschaft, die wiederum ein Objekt von einer hierarchischen Wesens beschreibt, das über Name, Typ und Wert verfügt.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Beschreibt einen Verweis an.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Beschreibt die Disassemblierung der IDE für die Anzeige.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Beschreibt eine Ausnahme oder ein Laufzeitfehler ausgegeben, die von der zu debuggende Programm wird ausgelöst.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Beschreibt eine lokale Variable, Parameter oder anderen Feldern.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Beschreibt einen Stapelrahmen.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Ein Array von eindeutigen Bezeichnern für verfügbare Debug-Engines beschreibt.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Verwendet die JustMyCode-Informationen für ein Modul festgelegt.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Beschreibt einen bestimmten Computer an.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Ein Arrayelement in einem Array beschreibt.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Beschreibt die Adresse eines Felds, einer Klasse oder Struktur.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Beschreibt die Adresse einer lokalen Variablen in einem Gültigkeitsbereich (in der Regel eine Funktion oder Methode).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Beschreibt die Adresse einer Methode einer Klasse.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Beschreibt einen Parameter einer Methode oder Funktion.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Beschreibt einen Rückgabewert einer Methode oder Funktion.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Beschreibt einen Feldtyp aus Metadaten erstellt.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Beschreibt ein bestimmtes Modul (DLL, EXE-Datei oder Assembly).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Beschreibt die Statusinformationen über die Symbolsuchpfade, die durchsucht wurden.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Beschreibt eine native Adresse an.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Beschreibt einen Feldtyp, ein Symbol für die PDB-Datei entnommen.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Beschreibt den Zustand eines Haltepunkts an, die an einen Speicherort gebunden werden kann.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Beschreibt einen Prozess an.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Beschreibt eine Liste der [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) programmknoten darstellende – Objekte.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Beschreibt die Prozesse, die auf einem Computer ausgeführt.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Beschreibt den Zeilen- und Spaltennummer Speicherort im angegebenen Text.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Beschreibt die Eigenschaften eines Threads.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Beschreibt ein Feld vom Typ.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Beschreibt eine physische Adresse an.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Beschreibt eine Adresse, die relativ zu einem `this` Zeiger (`Me` in Visual Basic).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h sh.h oder ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [API-Referenz](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
