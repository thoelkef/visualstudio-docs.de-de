---
title: "Erste Schritte (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".dbg-Dateien"
  - "DBG-Dateien"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Erste Schritte (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Debuggen von Zubehör des Schnittstellen\-Zugriffs \(SDK\) Durchmesser Dokumentation und \- Anweisung mit Sie ein Beispiel, das illustriert, wie der Durchmesser APIs verwendet.  Verwenden Sie die Schnittstellen und Methoden in DIA SDK, um benutzerdefinierte Anwendungen zu entwickeln, die die .pdb\- und .dbg\-Dateien öffnen und ihren Inhalt für Symbole, Werte, Attribute, Adressen und anderen Debuginformationen gefunden werden.  Dieses SDK stellt außerdem die Tabelle Orders der Verweise für die Eigenschaften bereit, die mit den Symbolen zugeordnet werden, die in C\+\+\-Anwendungen gefunden werden.  
  
 Zur optimalen Verwendung der DIA SDK, sollten Sie mit folgendem vertraut sein:  
  
-   C\+\+\-Programmiersprache  
  
-   COM\-Programmierung  
  
-   Die integrierte Entwicklungsumgebung \(IDE\) von Visual Studio zum Kompilieren der Beispiele  
  
 Das DIA SDK wird normalerweise mit Visual Studio installiert und seinem Standardspeicherort ist *\[Laufwerk\]*\\ Programme \\ Microsoft Visual Studio 9.0 \\ SDK DIA.  Im Rahmen der Installation wird das msdia90.dll, das das DIA SDK implementiert, automatisch alle so registriert, die Sie ausführen müssen, um es zu verwenden, das `dia2.h` , und im Programm im Link zu `diaguids.lib`eingeschlossen ist.  
  
 Header: dia2.h \\ Include  
  
 Bibliothek: \\ lib diaguids.lib  
  
 DLLs: bin \\ msdia80.dll  
  
 IDL\-Datei: dia2.idl \\ idl  
  
## In diesem Abschnitt  
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Wiederholt die grundlegende Architektur der Durchmesser.  
  
 [Abfragen der PDB\-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Stellt schrittweise Anweisungen darüber bereit, wie der Durchmesser API verwendet, um eine PDB\-Datei abzufragen.  
  
## Siehe auch  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)