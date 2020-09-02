---
title: Schnittstellen (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5eaf63ac57610e9ebde6703f0b5c15bf9607fdde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150872"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Schnittstellen (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Methoden werden alphabetisch unter jeder Schnittstelle im Inhaltsverzeichnis und auf der Schnittstellen Seite in der Vtable-Reihenfolge aufgelistet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Bietet die Kontrolle darüber, wie die Dia SDK virtuelle und relative virtuelle Adressen für Debug-Objekte berechnet.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Initiiert den Zugriff auf eine Quelle von Debugsymbolen.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Ermöglicht den Zugriff auf die Datensätze in einem Debug-Datenstrom.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Listet die verschiedenen debugstreams auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Listet die verschiedenen Frame-Datenelemente auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Listet die verschiedenen injizierten Quellen auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Listet die verschiedenen Zeilennummern auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Listet die verschiedenen Abschnitts Beiträge auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Listet die verschiedenen Segmente auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Listet die verschiedenen Quelldateien auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Listet die verschiedenen verfügbaren Stapel Rahmen auf.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Listet die verschiedenen Symbole auf, die in der Datenquelle enthalten sind.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Listet die verschiedenen in der Datenquelle enthaltenen Symbole auf.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Listet die verschiedenen Tabellen auf, die in der Datenquelle enthalten sind.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Macht die Details eines Stapel Rahmens verfügbar.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Macht die Details des Basis Speicher Orts und der Speicher Offsets des Moduls oder Bilds verfügbar.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Greift auf den in der Dia-Datenquelle gespeicherten Programm Quellcode zu.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Greift auf Informationen zu, die den Prozess der Zuordnung von einem Byteblock von Bildtext zu einer Quelldatei-Zeilennummer beschreiben.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Empfängt Rückrufe aus dem Dia-Symbol zum Suchen der Prozedur und ermöglicht so eine Benutzeroberfläche, um den Status des Orts Versuchs zu melden.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Empfängt Rückrufe aus dem Dia-Symbol zum Suchen von Prozeduren und ermöglicht das Erzwingen von Einschränkungen für den suchen.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Ermöglicht das Lesen der persistenten Eigenschaften eines Dia-Eigenschaften Satzes.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Ermöglicht es einer Client Anwendung, Bytes einer ausführbaren Datei anzugeben, wie in der Dateiposition angegeben.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Ermöglicht es einer Client Anwendung, Bytes einer ausführbaren Datei bereitzustellen, wie durch eine relative virtuelle Adresse angegeben.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Ruft Daten ab, die einen Abschnitts Beitrag beschreiben, d. h. ein zusammenhängender Speicherblock, der durch eine kompisierung zum Image beigetragen hat.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Ordnet Daten aus der Abschnitts Nummer den Segmenten des Adressraums zu.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Stellt einen Abfrage Kontext für Debugsymbole bereit.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Stellt eine Quelldatei dar.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Macht die Eigenschaften eines Stapel Rahmens verfügbar.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Stellt Methoden bereit, um einen Stapel Durchlauf mithilfe der PDB-Datei durchzuführen.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Verwaltet den Stapel Kontext zwischen Aufrufen der [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) -Methode.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Ermöglicht das Durchlaufen des Stapels mithilfe der Programm Debug-Datenbankdatei (PDB).  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Beschreibt die Eigenschaften einer Symbol Instanz.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Listet eine Dia-Datenquellen Tabelle auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Beschreibt die Enumerationen und Strukturen, die von den verschiedenen Schnittstellen der DIA SDK verwendet werden.  
  
 [Konstanten (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Beschreibt die Konstanten, die im Dia SDK verfügbar sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Referenz](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
