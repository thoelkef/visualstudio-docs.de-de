---
title: Getting Started (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164173"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Erste Schritte (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Dia-SDK (Debug Interface Access) stellt Ihnen eine Anleitungs Dokumentation und ein Beispiel zur Verfügung, das die Verwendung der Dia-API veranschaulicht. Verwenden Sie die Schnittstellen und Methoden in der DIA SDK, um benutzerdefinierte Anwendungen zu entwickeln, die die PDB-und dbg-Dateien öffnen, und Durchsuchen Sie Ihren Inhalt nach Symbolen, Werten, Attributen, Adressen und anderen Debuginformationen. Dieses SDK stellt auch Referenztabellen für die Eigenschaften bereit, die Symbolen in C++-Anwendungen zugeordnet sind.  
  
 Um die Dia SDK bestmöglich zu nutzen, sollten Sie mit folgenden Informationen vertraut sein:  
  
- Programmiersprache C++  
  
- COM-Programmierung  
  
- Integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio zum Kompilieren der Beispiele  
  
  Die Dia SDK wird normalerweise mit Visual Studio installiert, und der Standard Speicherort ist *[Laufwerk]* \Programme\Microsoft Visual Studio 9.0 \ Dia SDK. Im Rahmen der-Installation wird der msdia90.dll, der die Dia SDK implementiert, automatisch registriert. Sie müssen daher nur `dia2.h` in Ihr Programm einschließen und mit verknüpfen `diaguids.lib` .  
  
  Header: include\dia2.h  
  
  Bibliothek: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Überprüft die grundlegende Architektur von Dia.  
  
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Enthält Schritt-für-Schritt-Anleitungen zur Verwendung der Dia-API zum Abfragen einer PDB-Datei.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
