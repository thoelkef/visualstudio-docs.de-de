---
title: Verwenden des DebuggerTypeProxy-Attributs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: af0f2521b2276d28b07a4712009c4c4ae85a4d2d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477887"
---
# <a name="using-debuggertypeproxy-attribute"></a>Verwenden des DebuggerTypeProxy-Attributs
<xref:System.Diagnostics.DebuggerTypeProxyAttribute> gibt einen Proxy bzw. Vertreter für einen Typ an und ändert die Art, wie dieser Typ in Debuggerfenstern angezeigt wird. Wenn Sie eine Variable, die einen Proxy hat anzeigen, wird der Proxy stellvertretend für den ursprünglichen Typ in der **anzeigen**. Im Debuggervariablenfenster werden nur die öffentlichen Member des Proxytyps angezeigt. Private Member werden nicht angezeigt.  
  
 Mögliche Zuweisungen dieses Attributs:  
  
-   Strukturen  
  
-   Klassen  
  
-   Assemblys  
  
 Eine Typproxyklasse muss über einen Konstruktor verfügen, der ein Argument des vom Proxy ersetzten Typs verwendet. Der Debugger erstellt immer dann eine neue Instanz der Typproxyklasse, wenn eine Variable des Zieltyps angezeigt werden muss. Dies kann sich auf die Leistung auswirken. Daher sollten Sie nicht mehr als unbedingt erforderlich mit dem Konstruktor arbeiten.  
  
 Zur Minimierung von Leistungseinbußen werden die Attribute des Anzeigeproxys des Typs nicht von der Ausdrucksauswertung untersucht, es sei denn, der Typ wird erweitert. Dies geschieht, wenn der Benutzer im Debuggerfenster auf das Plussymbol (+) klickt bei Verwendung des <xref:System.Diagnostics.DebuggerBrowsableAttribute>-Attributs. Deshalb sollten Sie dem Anzeigetyp selbst keine Attribute hinzufügen. Attribute können und sollen im Text des Anzeigetyps verwendet werden.  
  
 Der Typproxy sollte eine private geschachtelte Klasse innerhalb der Klasse sein, auf die das Attribut abzielt. Dadurch ist der Zugriff auf interne Member problemlos möglich.  
  
 Wenn <xref:System.Diagnostics.DebuggerTypeProxyAttribute> auf der Assemblyebene verwendet wird, gibt der `Target`-Parameter den durch den Proxy ersetzten Typ an.  
  
 Ein Beispiel zur Verwendung dieses Attributs zusammen mit <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, finden Sie unter[mithilfe des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Verwenden von Generika mit DebuggerTypeProxy  
 Die Unterstützung für Generika ist eingeschränkt. In C# unterstützt `DebuggerTypeProxy` nur offene Typen. Ein offener Typ, d. h. ein nicht konstruierter Typ, ist ein generischer Typ, der nicht mit Argumenten für seine Typparameter instanziiert wurde. Geschlossene Typen, d. h. konstruierte Typen, werden nicht unterstützt.  
  
 Die Syntax für einen offenen Typ sieht wie folgt aus:  
  
 `Namespace.TypeName<,>`  
  
 Wenn Sie in `DebuggerTypeProxy` einen generischen Typ als Ziel angeben, müssen Sie diese Syntax verwenden. Der `DebuggerTypeProxy`-Mechanismus leitet die Typparameter für Sie her.  
  
 Weitere Informationen zu offenen und geschlossenen Typen in c# finden Sie unter der [c#-Programmiersprachenspezifikation](/dotnet/csharp/language-reference/language-specification), im Abschnitt 20.5.2 über offene und geschlossene Typen.  
  
 In Visual Basic gibt es keine Syntax für offene Typen. Daher ist dies in Visual Basic nicht möglich. Stattdessen müssen Sie eine Zeichenfolgendarstellung für den Namen des offenen Typs verwenden.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Erstellen Sie benutzerdefinierter Ansichten von .managed-Objekte](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Verbessern des Debuggens mit den Debuggeranzeigeattributen](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)