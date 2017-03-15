---
title: "Verwenden des DebuggerTypeProxy-Attributs | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Attribute [C#], Debugger"
  - "DebuggerTypeProxy-Attribut"
  - "DebuggerTypeProxyAttribute-Klasse"
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Verwenden des DebuggerTypeProxy-Attributs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> gibt einen Proxy bzw. Vertreter für einen Typ an und ändert die Art, wie dieser Typ in Debuggerfenstern angezeigt wird.  Wenn Sie eine Variable mit einem Proxy anzeigen, wird der Proxy stellvertretend für den ursprünglichen Typ in der **Anzeige** dargestellt.  Im Debuggervariablenfenster werden nur die öffentlichen Member des Proxytyps angezeigt.  Private Member werden nicht angezeigt.  
  
 Mögliche Zuweisungen dieses Attributs:  
  
-   Strukturen  
  
-   Klassen  
  
-   Assemblys  
  
 Eine Typproxyklasse muss über einen Konstruktor verfügen, der ein Argument des vom Proxy ersetzten Typs verwendet.  Der Debugger erstellt immer dann eine neue Instanz der Typproxyklasse, wenn eine Variable des Zieltyps angezeigt werden muss.  Dies kann sich auf die Leistung auswirken.  Daher sollten Sie nicht mehr als unbedingt erforderlich mit dem Konstruktor arbeiten.  
  
 Zur Minimierung von Leistungseinbußen werden die Attribute des Anzeigeproxys des Typs nicht von der Ausdrucksauswertung untersucht, es sei denn, der Typ wird erweitert. Dies geschieht, wenn der Benutzer im Debuggerfenster auf das Plussymbol \(\+\) klickt bei Verwendung des <xref:System.Diagnostics.DebuggerBrowsableAttribute>\-Attributs.  Deshalb sollten Sie dem Anzeigetyp selbst keine Attribute hinzufügen.  Attribute können und sollen im Text des Anzeigetyps verwendet werden.  
  
 Der Typproxy sollte eine private geschachtelte Klasse innerhalb der Klasse sein, auf die das Attribut abzielt.  Dadurch ist der Zugriff auf interne Member problemlos möglich.  
  
 Wenn <xref:System.Diagnostics.DebuggerTypeProxyAttribute> auf der Assemblyebene verwendet wird, gibt der `Target`\-Parameter den durch den Proxy ersetzten Typ an.  
  
 Ein Beispiel für die Verwendung dieses Attributs in Verbindung mit <xref:System.Diagnostics.DebuggerDisplayAttribute> und <xref:System.Diagnostics.DebuggerTypeProxyAttribute> finden Sie unter: [Verwenden des DebuggerDisplay\-Attributs](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## Verwenden von Generika mit DebuggerTypeProxy  
 Die Unterstützung für Generika ist eingeschränkt.  In C\# unterstützt `DebuggerTypeProxy` nur offene Typen.  Ein offener Typ, d. h. ein nicht konstruierter Typ, ist ein generischer Typ, der nicht mit Argumenten für seine Typparameter instanziiert wurde.  Geschlossene Typen, d. h. konstruierte Typen, werden nicht unterstützt.  
  
 Die Syntax für einen offenen Typ sieht wie folgt aus:  
  
 `Namespace.TypeName<,>`  
  
 Wenn Sie in `DebuggerTypeProxy` einen generischen Typ als Ziel angeben, müssen Sie diese Syntax verwenden.  Der `DebuggerTypeProxy`\-Mechanismus leitet die Typparameter für Sie her.  
  
 Weitere Informationen zu offenen und geschlossenen Typen in C\# finden Sie unter [C\#\-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification) im Abschnitt 20.5.2 über offene und geschlossene Typen.  
  
 In Visual Basic gibt es keine Syntax für offene Typen. Daher ist dies in Visual Basic nicht möglich.  Stattdessen müssen Sie eine Zeichenfolgendarstellung für den Namen des offenen Typs verwenden.  
  
 `"Namespace.TypeName'2"`  
  
## Siehe auch  
 [Verwenden des DebuggerDisplay\-Attributs](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Anzeigen von benutzerdefinierten Datentypen](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)