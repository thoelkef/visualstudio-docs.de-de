---
title: Überschreiben und Erweitern der generierten Klassen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 3ea0446d53ad3cc74bd8af96e95fabada1098da5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53929279"
---
# <a name="override-and-extend-the-generated-classes"></a>Außer Kraft setzen, und Erweitern der generierten Klassen

Ihrer DSL-Definition ist eine Plattform, auf der Sie einen Reihe leistungsstarken Tools erstellen können, die auf eine domänenspezifische Sprache basieren. Viele Erweiterungen und Anpassungen können vorgenommen werden, indem überschreiben und erweitern die Klassen, die von der DSL-Definition generiert werden. Diese Klassen umfassen nicht nur die Domänenklassen, die Sie explizit in der DSL-Definitionsdiagramm definiert haben, sondern auch andere Klassen, die definieren, die Toolbox, Explorer, Serialisierung und So weiter.

## <a name="extensibility-mechanisms"></a>Mechanismen zur Erweiterbarkeit

Mehrere Mechanismen werden bereitgestellt, damit Sie den generierten Code erweitern können.

### <a name="override-methods-in-a-partial-class"></a>Methoden in einer partiellen Klasse außer Kraft setzen

Partielle Klassendefinitionen ermöglichen eine Klasse in mehr als einem Ort definiert werden. Dadurch können Sie den generierten Code aus dem Code zu trennen, die Sie selbst schreiben. Im Code manuell geschrieben können Sie des generierten Codes geerbte Klassen überschreiben.

Wenn in Ihrer DSL-Definition Bereich definieren Sie eine Domänenklasse, die mit dem Namen z. B. `Book`, Sie benutzerdefinierten Code schreiben, der Methoden zum Überschreiben wird hinzugefügt:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Um Methoden in einer generierten Klasse zu überschreiben, Schreiben von Code immer in eine Datei, die von die generierten Dateien getrennt ist. In der Regel ist die Datei in einem Ordner enthalten, mit dem Namen CustomCode. Wenn Sie Änderungen an den generierten Code vornehmen, geht diese verloren, wenn Sie den Code aus der DSL-Definition erneut generieren.

Geben Sie zum Ermitteln von welche Methoden Sie außer Kraft setzen können **überschreiben** in der Klasse, gefolgt von einem Leerzeichen. Die IntelliSense-QuickInfo informiert Sie, welche Methoden überschrieben werden können.

### <a name="double-derived-classes"></a>Doppelte abgeleitete Klassen

Die meisten Methoden in der generierten Klassen werden vom einen festen Satz von Klassen in den Namespaces Modellierung geerbt. Allerdings werden einige Methoden im generierten Code definiert. Normalerweise bedeutet dies, dass Sie sie überschreiben nicht möglich; Sie können nicht in einer partiellen Klasse die Methoden überschreiben, die in einer anderen partiellen Definition der Klasse definiert werden.

Dennoch können Sie diese Methoden überschreiben, durch Festlegen der **generiert doppelte Ableitungen** Flag für die Domänenklasse. Dieser bewirkt, dass zwei Klassen generiert werden, wird eine abstrakte Basisklasse der anderen. Alle Methoden- und Eigenschaftendefinitionen sind in der Basisklasse und nur der Konstruktor in der abgeleiteten Klasse ist.

Im Beispiel Library.dsl, z. B. die `CirculationBook` Domänenklasse besitzt die `Generates``Double Derived` -Eigenschaftensatz auf `true`. Der generierte Code für diese Domänenklasse enthält zwei Klassen:

-   `CirculationBookBase`, dies ist eine abstrakte und alle Methoden und Eigenschaften enthält.

-   `CirculationBook`, ergibt sich aus `CirculationBookBase`. Er ist leer, mit Ausnahme der Konstruktoren.

Um eine beliebige Methode überschreiben, Sie erstellen eine partielle Definition der abgeleiteten Klasse wie z. B. `CirculationBook`. Sie können sowohl für die generierten Methoden als auch für den von der Modellierung Framework geerbten Methoden überschreiben.

Sie können diese Methode mit allen Arten von Element, einschließlich von Modellelementen, Beziehungen, Formen, Diagramme und Connectors verwenden. Sie können auch die Methoden der anderen generierten Klassen überschreiben. Einige Klassen generiert, wie z. B. die ToolboxHelper immer Double-Wert-abgeleitet sind.

### <a name="custom-constructors"></a>Benutzerdefinierten Konstruktoren

Einen Konstruktor kann nicht überschrieben werden. Selbst in Double abgeleiteten Klassen muss der Konstruktor in der abgeleiteten Klasse sein.

Wenn Sie Ihre eigenen Konstruktor bereitstellen möchten, erreichen Sie dies durch Festlegen von `Has Custom Constructor` für die Domänenklasse in der DSL-Definition. Beim Klicken auf **alle Vorlagen transformieren**, der generierte Code wird einen Konstruktor für diese Klasse nicht enthalten. Es umfasst einen Aufruf an den Konstruktor fehlt. Dies bewirkt, dass einen Fehlerbericht, wenn Sie die Projektmappe zu erstellen. Doppelklicken Sie auf den Fehlerbericht, um einen Kommentar im generierten Code zu lesen, die erklärt, was Sie bereitstellen sollten.

Schreiben Sie eine partielle Klassendefinition in einer Datei, die von die generierten Dateien getrennt ist, und geben Sie den Konstruktor.

### <a name="flagged-extension-points"></a>Gekennzeichnete Erweiterungspunkte

Ein gekennzeichnete Erweiterungspunkt ist eine Stelle in der DSL-Definition, in dem Sie festlegen können, eine Eigenschaft oder ein Kontrollkästchen, um anzugeben, dass Sie eine benutzerdefinierte Methode bereitstellen. Benutzerdefinierte Konstruktoren sind ein Beispiel. Weitere Beispiele umfassen die Einstellung der `Kind` einer Domäneneigenschaft berechnete oder benutzerdefinierte Speicher oder die Einstellung der **ist Benutzerdefiniert** -Flag in einem Verbindungs-Generator.

Beim Generieren von Code und legen Sie das Flag, wird in jedem Fall ein Buildfehler führen. Doppelklicken Sie auf den Fehler, um einen Kommentar zu lesen, der erklärt, was Sie bereitstellen müssen.

### <a name="rules"></a>Regeln

Der Transaktions-Manager können Sie Regeln definieren, die vor dem Ende einer Transaktion ausgeführt, in dem ein angegebenen Ereignisses, z. B. eine Änderung einer Eigenschaft aufgetreten ist. Regeln werden in der Regel verwendet, um Synchronism zwischen verschiedenen Elementen im Speicher zu verwalten. Beispielsweise werden Regeln verwendet, um sicherzustellen, dass es sich bei das Diagramm mit den aktuellen Zustand des Modells angezeigt.

Regeln werden auf Basis einer pro-Klasse, definiert, damit Sie nicht verfügen, damit der Code registriert, die die Regel für jedes Objekt. Weitere Informationen finden Sie unter [Regeln weitergegeben werden Änderungen in das Modell](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Store-Ereignisse

Der Modellierung Store bietet es sich um einen Ereignismechanismus, den Sie verwenden, um für bestimmte Typen von Änderungen im Speicher, einschließlich hinzufügen und Löschen von Elementen, Änderungen an Eigenschaftswerten, überwachen und so weiter. Der Ereignishandler werden nach Abschluss der Transaktion aufgerufen, in denen die Änderungen vorgenommen wurden. In der Regel werden diese Ereignisse verwendet, um Ressourcen außerhalb des Speichers zu aktualisieren.

### <a name="net-events"></a>Ereignisse für .NET

Sie können einige Ereignisse auf Formen abonnieren. Beispielsweise können Sie auf Mausklicks auf einer Form lauschen. Sie müssen Code schreiben, der das Ereignis für jedes Objekt abonniert. Dieser Code kann in einer Außerkraftsetzung der InitializeInstanceResources() geschrieben werden.

Einige Ereignisse werden auf ShapeFields, generiert, die zum Zeichnen von Decorator-Elemente auf einer Form verwendet werden. Ein Beispiel finden Sie unter [Vorgehensweise: Abfangen eines Klicks auf eine Form oder einen Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Diese Ereignisse werden in der Regel nicht innerhalb einer Transaktion ausgeführt. Wenn Sie Änderungen an den Store vornehmen möchten, sollten Sie eine Transaktion erstellen.