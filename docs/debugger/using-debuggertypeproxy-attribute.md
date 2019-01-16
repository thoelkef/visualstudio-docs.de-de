---
title: Verwenden des DebuggerTypeProxy-Attributs | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f868041449e622ddbd5cf177a0aa22771fd48498
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227537"
---
# <a name="using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>Verwenden des DebuggerTypeProxy-Attributs (C#, Visual Basic, C++ / CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> gibt einen Proxy bzw. Vertreter für einen Typ an und ändert die Art, wie dieser Typ in Debuggerfenstern angezeigt wird. Wenn Sie eine Variable mit einem Proxy anzeigen, wird der Proxy stellvertretend für den ursprünglichen Typ in der **Anzeige** dargestellt. Im Debuggervariablenfenster werden nur die öffentlichen Member des Proxytyps angezeigt. Private Member werden nicht angezeigt.

Mögliche Zuweisungen dieses Attributs:

- Strukturen
- Klassen
- Assemblys

> [!NOTE]
> Dieses Attribut wird unterstützt für nativen Code nur in C++ / CLI-Code.

Eine Typproxyklasse muss über einen Konstruktor verfügen, der ein Argument des vom Proxy ersetzten Typs verwendet. Der Debugger erstellt immer dann eine neue Instanz der Typproxyklasse, wenn eine Variable des Zieltyps angezeigt werden muss. Dies kann sich auf die Leistung auswirken. Daher sollten Sie nicht mehr als unbedingt erforderlich mit dem Konstruktor arbeiten.

Zur Minimierung von Leistungseinbußen werden die Attribute des Anzeigeproxys des Typs nicht von der Ausdrucksauswertung untersucht, es sei denn, der Typ wird erweitert. Dies geschieht, wenn der Benutzer im Debuggerfenster auf das Plussymbol (+) klickt bei Verwendung des <xref:System.Diagnostics.DebuggerBrowsableAttribute>-Attributs. Deshalb sollten Sie dem Anzeigetyp selbst keine Attribute hinzufügen. Attribute können und sollen im Text des Anzeigetyps verwendet werden.

Der Typproxy sollte eine private geschachtelte Klasse innerhalb der Klasse sein, auf die das Attribut abzielt. Dadurch ist der Zugriff auf interne Member problemlos möglich.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> können geerbt werden, wenn ein Typproxy in einer Basisklasse angegeben ist es für keine abgeleiteten Klassen, wendet es sei denn, diese abgeleiteten Klassen Geben Sie ihre eigenen Typproxy.

Wenn <xref:System.Diagnostics.DebuggerTypeProxyAttribute> auf der Assemblyebene verwendet wird, gibt der `Target`-Parameter den durch den Proxy ersetzten Typ an.

Ein Beispiel zur Verwendung dieses Attributs zusammen mit <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, finden Sie unter[Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).

## <a name="using-generics-with-debuggertypeproxy"></a>Verwenden von Generika mit DebuggerTypeProxy

Die Unterstützung für Generika ist eingeschränkt. In C# unterstützt `DebuggerTypeProxy` nur offene Typen. Ein offener Typ, d. h. ein nicht konstruierter Typ, ist ein generischer Typ, der nicht mit Argumenten für seine Typparameter instanziiert wurde. Geschlossene Typen, d. h. konstruierte Typen, werden nicht unterstützt.

Die Syntax für einen offenen Typ sieht wie folgt aus:

`Namespace.TypeName<,>`

Wenn Sie in `DebuggerTypeProxy` einen generischen Typ als Ziel angeben, müssen Sie diese Syntax verwenden. Der `DebuggerTypeProxy`-Mechanismus leitet die Typparameter für Sie her.

Weitere Informationen zu offenen und geschlossenen Typen in C# finden Sie unter den [ C# Sprachspezifikation](/dotnet/csharp/language-reference/language-specification), im Abschnitt 20.5.2 über offene und geschlossene Typen.

In Visual Basic gibt es keine Syntax für offene Typen. Daher ist dies in Visual Basic nicht möglich. Stattdessen müssen Sie eine Zeichenfolgendarstellung für den Namen des offenen Typs verwenden.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>Siehe auch

- [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)
- [Erstellen benutzerdefinierter Ansichten von verwalteten Objekten](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
