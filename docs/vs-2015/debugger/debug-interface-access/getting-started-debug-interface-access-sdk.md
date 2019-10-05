---
title: Erste Schritte (Debug Interface Access SDK) | Microsoft-Dokumentation
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68164173"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Erste Schritte (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Debug Interface Access (DIA) SDK stellt Sie bereit, mit dem Lehrzwecken Dokumentation und ein Beispiel, das veranschaulicht, wie Sie die DIA-API verwenden. Verwenden Sie die Schnittstellen und Methoden in DIA-SDK zum Entwickeln von benutzerdefinierter Anwendungen, die die PDB-Datei und .dbg-Dateien öffnen, und suchen Sie ihre Inhalte für Symbole, Werte, Attribute, Adressen und andere Debugginginformationen. Dieses SDK stellt außerdem Verweistabellen für die Eigenschaften für Symbole finden Sie in der C++-Anwendungen.  
  
 Um die DIA-SDK zu verwenden, sollten Sie mit folgendem vertraut sein:  
  
- Programmiersprache C++  
  
- COM-Programmierung  
  
- Visual Studio integrierte Entwicklungsumgebung (IDE) für die Beispiele kompilieren  
  
  Die DIA-SDK wird normalerweise mit Visual Studio installiert und wird von seinem Standardspeicherort *[Laufwerk]* \Programme\Microsoft Visual Studio-9.0\DIA SDK. Im Rahmen der Installation wird der "MSDIA90.dll", das die DIA-SDK implementiert, wird automatisch registriert, daher müssen Sie es verwenden sollen `dia2.h` in Ihrem Programm und Verknüpfung mit `diaguids.lib`.  
  
  Header: include\dia2.h  
  
  Bibliothek: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Überprüft die grundlegende Architektur von Dia  
  
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Enthält schrittweise Anleitungen zur Verwendung der DIA-API zum Abfragen der PDB-Datei an.  
  
## <a name="see-also"></a>Siehe auch  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
