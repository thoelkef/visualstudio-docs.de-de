---
title: Verwenden des DebuggerTypeProxy-Attributs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f7b404253c2425a64fd2a9ad4bb53943e033d8e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898836"
---
# <a name="using-debuggertypeproxy-attribute"></a>Verwenden des DebuggerTypeProxy-Attributs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DebuggerTypeProxyAttribute] (assetId:///T:System.Diagnostics.DebuggerTypeProxyAttribute?qualifyHint=False & AutoUpgrade = True) gibt einen Proxy bzw. Vertreter für einen Typ an und ändert die Art der Typ in Debuggerfenstern angezeigt wird. Wenn Sie eine Variable, die über einen Proxy verfügt anzeigen, wird der Proxy stellvertretend für den ursprünglichen Typ in der **anzeigen**. Im Debuggervariablenfenster werden nur die öffentlichen Member des Proxytyps angezeigt. Private Member werden nicht angezeigt.  
  
 Mögliche Zuweisungen dieses Attributs:  
  
- Strukturen  
  
- Klassen  
  
- Assemblys  
  
  Eine Typproxyklasse muss über einen Konstruktor verfügen, der ein Argument des vom Proxy ersetzten Typs verwendet. Der Debugger erstellt immer dann eine neue Instanz der Typproxyklasse, wenn eine Variable des Zieltyps angezeigt werden muss. Dies kann sich auf die Leistung auswirken. Daher sollten Sie nicht mehr als unbedingt erforderlich mit dem Konstruktor arbeiten.  
  
  Zur Minimierung von Leistungseinbußen werden die Attribute des Anzeigeproxys des Typs nicht von der Ausdrucksauswertung untersucht, es sei denn, der Typ wird erweitert. Dies geschieht, wenn der Benutzer im Debuggerfenster auf das Plussymbol (+) klickt bei Verwendung des <xref:System.Diagnostics.DebuggerBrowsableAttribute>-Attributs. Deshalb sollten Sie dem Anzeigetyp selbst keine Attribute hinzufügen. Attribute können und sollen im Text des Anzeigetyps verwendet werden.  
  
  Der Typproxy sollte eine private geschachtelte Klasse innerhalb der Klasse sein, auf die das Attribut abzielt. Dadurch ist der Zugriff auf interne Member problemlos möglich.  
  
  Wenn <xref:System.Diagnostics.DebuggerTypeProxyAttribute> auf der Assemblyebene verwendet wird, gibt der `Target`-Parameter den durch den Proxy ersetzten Typ an.  
  
  Ein Beispiel zur Verwendung dieses Attributs zusammen mit <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, finden Sie unter[Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## <a name="using-generics-with-debuggertypeproxy"></a>Verwenden von Generika mit DebuggerTypeProxy  
 Die Unterstützung für Generika ist eingeschränkt. In C# unterstützt `DebuggerTypeProxy` nur offene Typen. Ein offener Typ, d. h. ein nicht konstruierter Typ, ist ein generischer Typ, der nicht mit Argumenten für seine Typparameter instanziiert wurde. Geschlossene Typen, d. h. konstruierte Typen, werden nicht unterstützt.  
  
 Die Syntax für einen offenen Typ sieht wie folgt aus:  
  
 `Namespace.TypeName<,>`  
  
 Wenn Sie in `DebuggerTypeProxy` einen generischen Typ als Ziel angeben, müssen Sie diese Syntax verwenden. Der `DebuggerTypeProxy`-Mechanismus leitet die Typparameter für Sie her.  
  
 Weitere Informationen zu offenen und geschlossenen Typen in c# finden Sie unter den [C#-Sprachspezifikation](http://msdn.microsoft.com/library/e5d5a5cc-636b-4bff-b9c8-a8edc6207c22), im Abschnitt 20.5.2 über offene und geschlossene Typen.  
  
 In Visual Basic gibt es keine Syntax für offene Typen. Daher ist dies in Visual Basic nicht möglich. Stattdessen müssen Sie eine Zeichenfolgendarstellung für den Namen des offenen Typs verwenden.  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)   
  [Verbessern des Debuggens mit den Debuggeranzeigeattributen](http://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)



