---
title: Erste Schritte (Debug Interface Access SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d0c3c6df3fc92370d939771a7e94334db7f2cfc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-debug-interface-access-sdk"></a>Erste Schritte (Debug Interface Access SDK)
Das Debug Interface Access (DIA) SDK liefert Anweisungstext Dokumentation und ein Beispiel, das veranschaulicht, wie die DIA-API verwenden. Verwenden Sie die Schnittstellen und Methoden in DIA-SDK, benutzerdefinierte Anwendungen entwickeln, die die PDB-Datei und .dbg-Dateien öffnen und ihre Inhalte für Symbole, Werte, Attribute, Adressen und andere Debuginformationen zu suchen. Dieses SDK bietet auch Verweistabellen für die Eigenschaften für die Symbole in C++-Anwendungen gefunden wurden.  
  
 Um das DIA SDK zu verwenden, sollten Sie mit folgendem vertraut sein:  
  
-   Die Programmiersprache C++  
  
-   COM-Programmierung  
  
-   Visual Studio integrierten Entwicklungsumgebung (IDE) für das Kompilieren der Beispiele  
  
 Das DIA SDK wird normalerweise mit Visual Studio installiert und wird von seinem Standardspeicherort *[Laufwerk]*\Programme\Microsoft Visual Studio 9.0\DIA SDK. Im Rahmen der Installation wird "MSDIA90.dll", das das DIA SDK implementiert, wird automatisch registriert, damit tun können, um es verwenden, müssen Sie lediglich einschließen `dia2.h` in Ihrem Programm und Verknüpfung mit `diaguids.lib`.  
  
 Header: include\dia2.h  
  
 Bibliothek: lib\diaguids.lib  
  
 DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Überprüft die grundlegende Architektur von DIA.  
  
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Enthält schrittweise Anleitungen zur Verwendung der DIA-API zum Abfragen der PDB-Datei an.  
  
## <a name="see-also"></a>Siehe auch  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)