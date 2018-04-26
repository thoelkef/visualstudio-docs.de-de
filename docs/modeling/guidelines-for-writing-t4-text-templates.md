---
title: Richtlinien für das Verfassen von T4-Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f96cea682699382b55b786001a175616c877804a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Richtlinien für das Verfassen von T4-Textvorlagen
Diese allgemeinen Richtlinien sind möglicherweise hilfreich, wenn beim Generieren von Programmcode oder anderen Anwendungsressourcen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sie können Regeln werden nicht behoben.

## <a name="guidelines-for-design-time-t4-templates"></a>Richtlinien für die Entwurfszeit T4-Vorlagen
 Zur Entwurfszeit T4-Vorlagen sind Vorlagen, die Generieren von Code in Ihrem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt zur Entwurfszeit. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Variable Aspekte der Anwendung zu generieren.
Codegenerierung eignet sich am besten für die Aspekte der Anwendung, die möglicherweise während des Projekts ändern oder zwischen verschiedenen Versionen der Anwendung ändert. Trennen Sie diese Variable Aspekte von mehr invarianten Aspekte, damit Sie leichter ermitteln können, was generiert werden muss. Wenn Ihre Anwendung eine Website bereitstellt, trennen Sie z. B. die Standardseite für die Funktionen von der Logik, die Navigationspfade auf einer Seite in eine andere definiert.

 Die Variable Aspekte in einem oder mehreren Quellmodellen zu codieren.
Ein Modell ist eine Datei oder Datenbank, die jede Vorlage gelesen wird, um bestimmte Werte für Variablen Teile des Codes zu erhalten, die generiert werden soll. Modelle können Datenbanken, XML-Dateien von Entwurf, Diagramme oder domänenspezifische Sprachen werden. Ein Modell wird in der Regel verwendet, um viele Dateien im generieren eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Jede Datei wird aus einer eigenen Vorlage generiert.

 Sie können mehr als ein Modell in einem Projekt verwenden. Beispielsweise können Sie ein Modell für die Navigation zwischen Webseiten und ein separates Modell für das Layout der Seiten definieren.

 Das Modell auf Anforderungen des Benutzers und das Vokabular, nicht auf Ihre Implementierung zu konzentrieren.
In einer Website-Anwendung würden Sie z. B. das Modell finden Sie Links zu Webseiten erwarten.

 Im Idealfall, wählen Sie eine Form der Präsentation, die die Art der Informationen am besten entspricht, die das Modell darstellt. Ein Modell der Navigationspfade über eine Website kann z. B. ein Diagramm mit Feldern und Pfeile sein.

 Testen Sie den generierten Code.
Verwenden Sie manuelle oder automatisierte Tests, um sicherzustellen, dass der resultierende Code funktioniert wie die Benutzer benötigen. Vermeiden Sie das Generieren von Tests aus dem gleichen Modell aus dem der Code generiert wird.

 In einigen Fällen können allgemeine Tests für das Modell direkt ausgeführt werden. Sie können z. B. einen Test schreiben, der sicherstellt, dass jeder Seite in der Website von der Navigation von einer anderen erreicht werden kann.

 Zulassen von benutzerdefiniertem Code: Generieren von partiellen Klassen.
Für Code, den Sie per hand katalogisiert wird darüber hinaus an den generierten Code schreiben können. Es ist bei einem Code-Generation-Schema in der Lage, alle möglichen Variationen berücksichtigen, die auftreten können. Aus diesem Grund sollten Sie erwarten, um Spalten hinzuzufügen bzw. Teil des generierten Codes zu überschreiben. Das generierte Material steht in einer .NET-Sprache wie z. B. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], zwei Strategien sind besonders nützlich:

-   Die generierten Klassen sollten partiell sein. Dadurch können Sie zum Hinzufügen von Inhalt an den generierten Code.

-   Klassen, die in-Paaren, einen erben von der anderen generiert werden soll. Die Basisklasse sollte alle generierten Methoden und Eigenschaften enthalten, und die abgeleitete Klasse sollte nur die Konstruktoren enthalten. Dadurch Hand geschriebener Code die generierten Methoden überschreiben.

 Verwenden Sie in anderen generierten Sprachen wie z. B. XML, die `<#@include#>` Direktive, um einfache Kombinationen von Hand geschriebene und generierten Inhalt zu erstellen. In komplexeren Fällen müssen Sie möglicherweise einen Nachverarbeitungsschritt schreiben, der die generierte Datei mit Hand geschriebene Dateien kombiniert.

 Allgemeine Material in Includedateien verschieben oder Laufzeitvorlagen vermeiden wiederholte ähnliche Blöcke von Text und Code in mehreren Vorlagen verwenden Sie die `<#@ include #>` Richtlinie. Weitere Informationen finden Sie unter [T4-Include-Direktive](../modeling/t4-include-directive.md).

 Sie können auch zur Laufzeit-Textvorlagen in einem separaten Projekt erstellen, und rufen sie dann aus der Vorlage zur Entwurfszeit. Verwenden Sie hierzu die `<#@ assembly #>` Richtlinie zum Zugreifen auf den separaten Projekt. Beispiele finden Sie unter ["Vererbung in Textvorlagen" im Blog von Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

 Erwägen Sie große Datenblöcke des Codes in einer separaten Assembly.
 Wenn Sie große Code- und Klassenfunktionsblöcke verfügen, könnte es nützlich sein Teil dieses Codes in Methoden zu verschieben, die Sie in einem separaten Projekt zusammenstellen. Sie können die `<#@ assembly #>` Richtlinie den Zugriff auf den Code in der Vorlage. Weitere Informationen finden Sie unter [T4-Assemblydirektive](../modeling/t4-assembly-directive.md).

 Sie können die Methoden in einer abstrakten Klasse einfügen, die die Vorlage erben kann. Die abstrakte Klasse erben muss <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Weitere Informationen finden Sie unter [T4-Template-Direktive](../modeling/t4-template-directive.md).

 Generieren von Code, nicht Konfiguration Dateien eine Methode zum Schreiben einer Variablen Anwendung generische Anwendung Code schreiben, der eine Konfigurationsdatei akzeptiert. Eine Anwendung, die auf diese Weise geschrieben ist sehr flexibel und kann neu konfiguriert werden, wenn die geschäftsanforderungen zu ändern, ohne die Anwendung neu zu erstellen. Ein Nachteil dieses Ansatzes ist jedoch, dass die Anwendung mit geringerer Leistung als eine spezifischere ausgeführt werden. Darüber hinaus wird der Programmcode möglicherweise schwieriger zu lesen und zu pflegen, teilweise hat immer für den Umgang mit der meisten generischen Typen.

 Im Gegensatz dazu kann eine Anwendung, deren Variablenteile vor der Kompilierung generiert werden, stark typisiert. Dies macht es viel einfacher und zuverlässiger Hand geschriebener Code schreiben und in die generierte integrieren, Teile der Software.

 Um alle Vorteile der codegenerierung zu erhalten, versuchen Sie, generieren Programmcode anstelle von Konfigurationsdateien.

 Verwenden Sie ein Ordner für generierten Code platzieren Sie die Vorlagen und die generierten Dateien in einem Projektordner mit dem Namen **generierten Code**, um ihn zu machen deutlich, dass keine Dateien sind, die direkt bearbeitet werden soll. Wenn Sie benutzerdefinierten Code überschrieben oder hinzugefügt werden, auf die generierten Klassen erstellen, platzieren Sie diese Klassen in einem Ordner mit dem Namen **benutzerdefinierten Code**. Die Struktur von einem typischen Projekt sieht folgendermaßen aus:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs

```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Richtlinien für die Run-Time (vorverarbeiteten) T4-Vorlagen
 Verschieben von allgemeinem Material in geerbte Vorlagen können Vererbung, um Methoden und Textblöcke zwischen T4-Textvorlagen zu nutzen. Weitere Informationen finden Sie unter [T4-Template-Direktive](../modeling/t4-template-directive.md).

 Sie können auch Includedateien, die über Laufzeitvorlagen verfügen.

 Verschieben Sie umfangreiche Codetexte in einer partiellen Klasse.
Jede Laufzeitvorlage generiert eine partielle Klassendefinition, die den gleichen Namen wie die Vorlage hat. Sie können eine Codedatei schreiben, die eine andere partielle Definition der Klasse enthält. Sie können Methoden, Felder und Konstruktoren der Klasse auf diese Weise hinzufügen. Diese Member können in den Codeblöcken in der Vorlage aufgerufen werden.

 Ein Vorteil dieser ist, dass der Code einfacher zu schreiben, weil IntelliSense verfügbar ist. Darüber hinaus können Sie eine bessere Trennung zwischen der Präsentations- und der zugrunde liegende Logik erzielen.

 Beispielsweise ist in **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 In **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 Zulassen von benutzerdefiniertem Code: Bereitstellen von Erweiterungspunkten ggf. Generieren von virtuelle Methoden in \<#+ Klassenfunktion blockiert #>. Dadurch wird eine einzelne Vorlage, die in vielen Kontexten unverändert verwendet werden. Anstelle der Vorlage ändern, können Sie eine abgeleitete Klasse erstellen, die die minimale zusätzliche Logik liefert. Die abgeleitete Klasse kann entweder regulären Code oder eine Laufzeitvorlage sind möglich.

 Beispielsweise ist in "MyStandardRunTimeTemplate.tt":

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 Im Code einer Anwendung:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();

```

## <a name="guidelines-for-all-t4-templates"></a>Richtlinien für alle T4-Vorlagen
 Separate Datensammlung aus textgenerierung versuchen, zu vermeiden, Berechnung und Textblöcke mischen. Verwenden Sie in jeder Textvorlage die erste \<#-Codeblock #> Festlegen von Variablen und komplexe Berechnungen ausführen. Aus der ersten TextBlock unten zum Ende der Vorlage oder die erste \<#+ Klassenfunktion blockieren #> vermeiden Sie lange Ausdrücke und zu vermeiden, Schleifen und Bedingungen, es sei denn, sie Textblöcke enthalten. Dieses Vorgehen stellt die Vorlage, die einfacher zu lesen und zu verwalten.

 Verwenden Sie keine `.tt` sind Dateien verwenden Sie eine andere Erweiterung wie `.ttinclude` nach Includedateien. Verwendung `.tt` nur für Dateien, die zur sollen als zur Laufzeit oder zur Entwurfszeit-Textvorlagen verarbeitet. In einigen Fällen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erkennt `.tt` -Dateien und deren Eigenschaften für die Verarbeitung automatisch festgelegt.

 Starten Sie jede Vorlage als festen Prototyp.
Schreiben Sie ein Beispiel des Codes oder der Text, die Sie verwenden möchten, generieren, und stellen Sie sicher, dass er korrekt ist. Ändern Sie ihre Erweiterung in TT und inkrementell fügen Sie Code, der den Inhalt durch Lesen des Modells ändert.

 Erwägen Sie typisierte Modelle.
Obwohl Sie ein XML-Index oder Datenbank-Schema für die Modelle erstellen können, möglicherweise es sinnvoll sein, eine domänenspezifische Sprache (DSL) erstellen. Eine DSL hat den Vorteil, dass es sich um eine Klasse zum Darstellen von jedem Knoten im Schema und Eigenschaften, die die Attribute darstellen generiert. Dies bedeutet, dass Sie in Bezug auf das Geschäftsmodell programmieren können. Zum Beispiel:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Erwägen Sie Diagramme für die Modelle.
Viele Modelle sind am effektivsten angezeigt und verwaltet einfach als Texttabellen, insbesondere dann, wenn sie sehr groß sind.

 Allerdings für einige Arten von geschäftsanforderungen, es ist wichtig, um zu verdeutlichen, komplexe Sätze von Beziehungen und Workflows aufgeführt und Diagramme sind die am besten geeignet Mittel. Ein Vorteil eines Diagramms ist, dass es problemlos mit Benutzern und anderen Projektbeteiligten besprochen werden. Generieren von Code aus einem Modell auf der Ebene der geschäftsanforderungen, stellen Sie Ihren Code flexibler bei Anforderungen geänderten.

 Sie können auch einen eigenen Typ des Diagramms als eine domänenspezifische Sprache (DSL) entwerfen. Code kann aus UML- und konzentriert generiert werden. Weitere Informationen finden Sie unter [analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Siehe auch

- [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)
