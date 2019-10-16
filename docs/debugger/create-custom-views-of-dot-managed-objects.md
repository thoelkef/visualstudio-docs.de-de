---
title: Erstellen benutzerdefinierter Ansichten von verwalteten Objekten | Microsoft-Dokumentation
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
ms.openlocfilehash: 4649ac11daa062089d2916a5d5d0a331e4d74272
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349459"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Erstellen benutzerdefinierter Ansichten von verwalteten ObjektenC#(Visual Basic, F#, C++/CLI)
Sie können die Art anpassen, wie Datentypen von Visual Studio in Debuggervariablenfenstern angezeigt werden.

## <a name="attributes"></a>Attribute

In C#, Visual Basic, F#und C++ (C++nur/CLI-Code) können Sie mithilfe von <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerBrowsableAttribute> Erweiterungen für benutzerdefinierte Daten hinzufügen.

In .NET Framework 2,0-Code unterstützt Visual Basic das DebuggerBrowsable-Attribut nicht. Diese Einschränkung wurde in aktuelleren Versionen von .NET Framework entfernt.

## <a name="visualizers"></a>Schnellansichten

Sie können eine Schnellansicht schreiben, um einen beliebigen verwalteten Datentyp anzuzeigen. Weitere Informationen finden Sie unter [Gewusst wie: Schreiben einer](/visualstudio/debugger/create-custom-visualizers-of-data)Schnellansicht.

> [!NOTE]
> Für C++ Code können Sie mit dem natvis-Framework benutzerdefinierte Datentyp Erweiterungen hinzufügen, wie in [Erstellen benutzerdefinierter C++ Ansichten von Objekten im Debugger](/visualstudio/debugger/create-custom-views-of-native-objects)beschrieben.

## <a name="see-also"></a>Siehe auch

- [Dem Debugger mitteilen, was mit dem DebuggerDisplay-Attribut angezeigt werden soll](../debugger/using-the-debuggerdisplay-attribute.md)
- [Hiermit wird dem Debugger mitgeteilt, welcher Typ mit dem DebuggerTypeProxy-Attribut angezeigt werden soll.](../debugger/using-debuggertypeproxy-attribute.md)
- [Fenster "Überwachen" und "Schnellüberwachung"](../debugger/watch-and-quickwatch-windows.md)
- [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
