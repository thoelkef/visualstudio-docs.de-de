---
title: Getting Started (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2dd6a98f377ba295d6a866c9db95671de4ff16ea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745102"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Erste Schritte (Debug Interface Access SDK)
Das Dia-SDK (Debug Interface Access) stellt Ihnen eine Anleitungs Dokumentation und ein Beispiel zur Verfügung, das die Verwendung der Dia-API veranschaulicht. Verwenden Sie die Schnittstellen und Methoden in der DIA SDK, um benutzerdefinierte Anwendungen zu entwickeln, die die PDB-und dbg-Dateien öffnen, und Durchsuchen Sie Ihren Inhalt nach Symbolen, Werten, Attributen, Adressen und anderen Debuginformationen. Dieses SDK stellt auch Referenztabellen für die Eigenschaften bereit, die den in C++ Anwendungen gefundenen Symbolen zugeordnet sind.

 Um die Dia SDK bestmöglich zu nutzen, sollten Sie mit folgenden Informationen vertraut sein:

- C++Programmiersprache

- COM-Programmierung

- Integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio zum Kompilieren der Beispiele

  Die Dia SDK wird normalerweise mit Visual Studio installiert, und der Standard Speicherort ist *[Laufwerk]* \Programme\Microsoft Visual Studio 9.0 \ Dia SDK. Im Rahmen der Installation wird die msdia90. dll, die die Dia SDK implementiert, automatisch registriert, sodass Sie nur die `dia2.h` in das Programm einschließen und mit `diaguids.lib` verknüpfen müssen.

  Header: include\dia2.h

  Bibliothek: lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>In diesem Abschnitt

[Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

Überprüft die grundlegende Architektur von Dia.

[Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Enthält Schritt-für-Schritt-Anleitungen zur Verwendung der Dia-API zum Abfragen einer PDB-Datei.

## <a name="see-also"></a>Siehe auch

- [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)