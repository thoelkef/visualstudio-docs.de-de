---
title: Erstellen von benutzerdefinierten Ansichten von verwalteten Objekten | Microsoft-Dokumentation
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
ms.openlocfilehash: f5247a56667f5715d9f155c662eb333967878d71
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188648"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Erstellen von benutzerdefinierten Ansichten von verwalteten Objekten (C#, Visual Basic, F#, C++/CLI)
Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.

## <a name="attributes"></a>Attribute

In C#, Visual Basic, F# und C++ (nur C++-/CLI-Code) können Sie Erweiterungen für benutzerdefinierte Daten mit <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerBrowsableAttribute> hinzufügen.

In .NET Framework 2.0-Code bietet Visual Basic keine Unterstützung des DebuggerBrowsable-Attributs. Diese Einschränkung wurde in aktuelleren Versionen von .NET entfernt.

## <a name="visualizers"></a>Schnellansichten

Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Schreiben einer Schnellansicht](create-custom-visualizers-of-data.md).

> [!NOTE]
> Für C++-Code können Sie mit dem Natvis-Framework benutzerdefinierte Datentyperweiterungen hinzufügen, wie unter [Erstellen benutzerdefinierter Ansichten von C++-Objekten im Debugger](create-custom-views-of-native-objects.md) beschrieben wird.

## <a name="see-also"></a>Siehe auch

- [Debugger mit dem DebuggerDisplay-Attribut anweisen, was angezeigt werden soll](../debugger/using-the-debuggerdisplay-attribute.md)
- [Debugger mit dem DebuggerTypeProxy-Attribut anweisen, welcher Typ angezeigt werden soll](../debugger/using-debuggertypeproxy-attribute.md)
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
