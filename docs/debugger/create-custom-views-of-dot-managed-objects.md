---
title: Erstellen benutzerdefinierte Ansichten von Objekten | Microsoft-Dokumentation
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 733f3ec7573287e934f8a5f0167db89c0683759a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564007"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Erstellen benutzerdefinierte Ansichten von Objekten (C#, Visual Basic C++)
Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.

## <a name="native-code"></a>nativer Code

Für C++ Code können Sie benutzerdefinierte Daten geben Erweiterungen, die mit dem Natvis-Framework hinzufügen, wie in beschrieben [Erstellen benutzerdefinierter Ansichten von C++ Objekte im Debugger](/visualstudio/debugger/create-custom-views-of-native-objects). Für C++/CLI-Code, außerdem können Sie hier in diesem Artikel beschriebenen Attribute.

## <a name="attributes"></a>Attribute

In C#, Visual Basic und C++ (C++nur /CLI Code), können Sie Erweiterungen für die Verwendung von benutzerdefinierter Daten hinzufügen <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, und <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

In [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]-Code bietet Visual Basic keine Unterstützung des DebuggerBrowsable-Attributs. Diese Einschränkung wurde in aktuelleren Versionen von .NET Framework entfernt.

## <a name="visualizers"></a>Schnellansichten

Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Schnellansicht](/visualstudio/debugger/create-custom-visualizers-of-data).

## <a name="see-also"></a>Siehe auch

- [Entsprechende Konfiguration des Debuggers Vorgehensweise wird die Verwendung des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)
- [Entsprechende Konfiguration des Debuggers, welcher Typ wird die Verwendung des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md)
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)