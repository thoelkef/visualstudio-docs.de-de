---
title: Debug Interface Access SDK | Microsoft-Dokumentation
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdc5a980c9019fdaf330db9602f0b8445456c7c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889565"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK

Das Microsoft Debug-Schnittstelle Zugriff Software Development Kit (DIA-SDK) bietet Zugriff auf in die Programmdateien der Programmdatenbankdatei (.pdb) von Microsoft-Postcompilertools generierten gespeicherten Informationen zu debuggen. Da das Format der von der Postcompilertools generierten PDB-Datei mit konstanter Revision durchgeführt wird, ist das Verfügbarmachen von Format unpraktisch. Verwenden die DIA-API, können Sie Anwendungen entwickeln, die suchen und Durchsuchen die Debuginformationen in PDB-Datei gespeichert. Solche Anwendungen können z. B. Stapel-Trace-Back-Berichtsinformationen und Analysieren von Leistungsdaten.

## <a name="in-this-section"></a>In diesem Abschnitt

[Erste Schritte](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
Bietet eine Übersicht über die DIA-SDK-Funktionen, und gibt an, wo die DIA-SDK sowie die erforderlichen Header und Bibliotheksdateien installiert ist.

[Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
Enthält Anweisungen zur Verwendung der DIA-API zum Abfragen der PDB-Datei an.

[Symbole und Symboltags](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
Erläutert, wie Symbole und symboltags in die DIA-API verwendet werden.

[Verweis](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
Enthält die Schnittstellen, Methoden, Enumerationen und Strukturen der DIA-API.

[Dia2dump-Beispiel](../../debugger/debug-interface-access/dia2dump-sample.md)  
Veranschaulicht, wie die DIA-API zu suchen und Durchsuchen von Informationen zum Debuggen.
