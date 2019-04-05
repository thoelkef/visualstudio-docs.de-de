---
title: Debugger-Benutzeroberfläche (XSLT) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1af3b47b2d7c897b36556f0ebac105088cdc9b75
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58962156"
---
# <a name="debugger-user-interface-xslt"></a>Benutzeroberfläche des XSLT-Debuggers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden die Fenster und Dialogfelder des Debuggers beschrieben. Es werden nur die Elemente der Benutzeroberfläche erläutert, die ein XSLT-spezifisches Debugverhalten aufweisen.  
  
 Weitere Informationen finden Sie unter den [Benutzeroberflächenreferenz Debuggen](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>Lokalfenster  
 Im Lokalfenster werden Informationen zu allen im Stylesheet definierten Variablen angezeigt. Das Lokalfenster enthält drei Spalten mit Informationen:  
  
 **Name**  
 Diese Spalte enthält die Namen aller lokalen Variablen im aktuellen Gültigkeitsbereich. Knotengruppen verfügen über eine Strukturansicht, die Sie erweitern können, um die Unterordner anzuzeigen.  
  
 **Wert**  
 In dieser Spalte wird für jede Variable der vorhandene Wert angezeigt. Für Attribut-, Verarbeitungsanweisungs-, Kommentar-, Text- und CDATA-Knoten wird der Textwert des Knotens angezeigt. Für Namespace-Knoten wird der Namespace-URI angezeigt.  
  
 **Type**  
 Diese Spalte identifiziert, den Datentyp der einzelnen Variablen aufgeführt, die der **Namen** Spalte.  
  
 Im Lokalfenster werden auch die vordefinierten Kontextvariablen angezeigt, mit denen der Kontext der XSLT-Transformation verfolgt wird. In der folgenden Tabelle werden die vom XSLT-Debugger verwendeten vordefinierten Kontextvariablen beschrieben.  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`last()`|Die Kontextgröße.|  
|`position()`|Die Position bzw. Indexnummer des Kontextknotens in Bezug auf die Kontextgröße.|  
|`self::node()`|Der Wert des Kontextknotens.|  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Ändern des Debugkontexts](http://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).  
  
## <a name="output-window"></a>Ausgabefenster  
 Im Ausgabefenster werden alle während des Debuggens ausgegebenen Fehlermeldungen und aufgetretenen Sicherheitsausnahmen angezeigt.  
  
 Die Debuggerausgabe wird vom XSLT-Debugger in einem separaten Fenster angezeigt. Dies ist dasselbe Fenster, zur Anzeige der Ausgabe aus einem **XSLT-Ausgabe anzeigen** Befehl.  
  
## <a name="task-list"></a>Aufgabenliste  
 In der Aufgabenliste werden alle Kompilierungsfehler im Stylesheet aufgelistet. Durch Doppelklicken auf den Fehler wird der Cursor auf der fehlerhaften Zeile platziert.  
  
 Die Aufgabenliste enthält alle Fehler, die in den Skriptblöcken in der XSLT-Datei auftreten.  
  
> [!NOTE]
>  Der XSLT-Debugger gibt keine Warnungen aus. Daher werden keine Warnungen in der Aufgabenliste angezeigt.  
  
## <a name="breakpoints-window"></a>Fenster "Haltepunkte"  
 Im Fenster Haltepunkte werden alle im aktuellen Projekt festgelegten Haltepunkte angezeigt. Wenn während der Anzeige dieses Fensters ein Haltepunkt hinzugefügt wird, wird das Fenster automatisch aktualisiert, sodass der neue Haltepunkt ebenfalls angezeigt wird.  
  
 Das Fenster Haltepunkte weist dasselbe Verhalten wie andere Debuggern von Visual Studio auf.  
  
## <a name="command-windowimmediate-window"></a>Befehlsfenster/Direktfenster  
 In diesem Release des XSLT-Debuggers nicht implementiert.  
  
## <a name="watch-window"></a>Überwachungsfenster  
 Das Überwachungsfenster wird zum Auswerten der Variablen verwendet. Sie können dort auch die Werte der Variablen ändern.  
  
 Die im Überwachungsfenster angezeigten Variablen beziehen sich auf den aktuellen Kontext (auf das oberste Element in der Aufrufliste). Beim Ändern des Kontexts wird das Überwachungsfenster aktualisiert, und es werden die für den betreffenden Kontext festgelegten Variablen angezeigt.  
  
## <a name="call-stack-window"></a>Aufruflistenfenster  
 Im Aufruflistenfenster werden die Namen der Funktionen in der Aufrufliste, die Parametertypen und Parameterwerte angezeigt. Aufruflisteninformationen werden nur angezeigt, wenn sich das derzeit debuggte Programm im Haltezustand befindet.  
  
 Die Aufrufliste stellt die verschiedenen Kontexte dar, die bei der XSLT-Ausführung durchlaufen werden. Wenn beispielsweise ein Aufruf der Vorlage "b" von der Vorlage "a" aus erfolgt, werden die Vorlagen "a" und "b" im Aufruflistenfenster mit dem aktuellen Kontext in der Liste an oberster Position angezeigt. Für den Benutzer wird die derzeit ausgeführte Abfrage angezeigt.  
  
 Wenn die Vorlagen in der XSLT-Datei keinen Namen aufweisen, werden die vom XSLT-Prozessor generierten Namen verwendet.  
  
 Wenn auf ein anderes Element als das Element an oberster Position in der Liste geklickt wird, wird dem Betrachter mithilfe der standardmäßigen grünen Hervorhebung und grünen Pfeile angezeigt, welche XSLT-Verzweigung gerade ausgeführt wird.  
  
## <a name="quickwatch-dialog-box"></a>Dialogfeld "Schnellüberwachung"  
 Die **Schnellüberwachung** Dialogfeld wird verwendet, um XPath 1.0-Ausdrücke ausgewertet werden. Der Kontextknoten (der `self::node()`-Knoten im Lokalfenster) stellt den Kontext für die Ausführung des XPath-Ausdrucks bereit. Das Ergebnis der Ausführung des XPath-Ausdrucks wird im Überwachungsfenster angezeigt.  
  
 In der folgenden Liste werden einige Einschränkungen für die Auswertung von XPath-Ausdrücken beschrieben.  
  
- Nur integrierte XPath-Funktionen sind zulässig.  
  
- Integrierte XPath-Funktionen (z. B. `document()`, `key()` usw.) sind nicht zulässig.  
  
- Benutzerdefinierte Funktionen sind nicht zulässig.  
  
  Weitere Informationen finden Sie unter [Vorgehensweise: Auswerten eines XPath-Ausdrucks](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Disassemblyfenster  
 Im Disassemblyfenster wird der vom XSLT-Compiler generierte Assemblycode angezeigt. Dieser Fenster kann in gleicher Weise wie alle anderen Disassemblyfenster in Visual Studio verwendet werden.  
  
 Weitere Informationen [Vorgehensweise: Verwenden des Disassembierungsfensters](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von XSLT](../xml-tools/debugging-xslt.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Variablenfenster](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
