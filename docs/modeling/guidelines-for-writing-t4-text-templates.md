---
title: Richtlinien für das Verfassen von T4-Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: a302eb05e6b4c763740f03baea4aa8bd41c72891
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959891"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Richtlinien für das Verfassen von T4-Textvorlagen
Diese allgemeinen Richtlinien ist möglicherweise hilfreich, wenn Sie Programmcode oder andere Ressourcen der Anwendung in Visual Studio generieren. Sie sind nicht die Regeln fest.

## <a name="guidelines-for-design-time-t4-templates"></a>Richtlinien für die Entwurfszeit-T4-Vorlagen
 Während der Entwurfszeit T4-Vorlagen sind Vorlagen, die Code in Visual Studio-Projekt zur Entwurfszeit zu generieren. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Generieren Sie die Variablen Teile der Anwendung.
Codegenerierung eignet sich am besten für die Aspekte der Anwendung, die möglicherweise während des Projekts ändern oder zwischen verschiedenen Versionen der Anwendung ändert. Trennen Sie diese Variablen Teile von mehr invariante Aspekte, damit Sie einfacher bestimmen können, was zu generiert hat. Wenn Ihre Anwendung eine Website bereitstellt, trennen Sie z. B. der Standardseite für die Funktionen von Logik, die Navigationspfade auf einer Seite zu einem anderen definiert.

 Codieren Sie die abweichenden Aspekte in einem oder mehreren Source-Modellen.
Ein Modell ist eine Datei oder Datenbank, die jeder Vorlage gelesen werden, um bestimmte Werte für Variablen Teile des Codes zu erhalten, die generiert werden soll. Modelle können sein, Datenbanken, XML-Dateien von Ihren eigenen Entwurf, Diagramme oder domänenspezifische Sprachen. In der Regel wird ein Modell verwendet, um viele Dateien in Visual Studio-Projekt zu generieren. Jede Datei wird aus einer getrennten Vorlage generiert.

 Sie können mehr als einem Modell in einem Projekt verwenden. Beispielsweise können Sie ein Modell für die Navigation zwischen Webseiten und ein separates Modell für das Layout der Seiten definieren.

 Das Modell auf Anforderungen des Benutzers und das Vokabular, nicht auf Ihre Implementierung zu konzentrieren.
In einer Websiteanwendung würden Sie z. B. das Modell zum Verweisen auf Webseiten und Hyperlinks erwarten.

 Wählen Sie im Idealfall eine Form der Präsentation, die die Art der Informationen geeignet ist, die das Modell darstellt. Ein Modell der Navigationspfade eine Website kann z. B. ein Diagramm von Feldern und Pfeilen sein.

 Testen Sie den generierten Code.
Verwenden Sie manuelle oder automatisierte Tests, um sicherzustellen, dass der resultierende Code funktioniert, wie die Benutzer benötigen. Vermeiden Sie das Generieren von Tests aus dem gleichen Modell aus dem der Code generiert wird.

 In einigen Fällen können allgemeine Tests direkt auf dem Modell durchgeführt werden. Beispielsweise können Sie einen Test schreiben, der sicherstellt, dass jede Seite auf der Website von der Navigation von einer anderen erreicht werden kann.

 Zulassen von benutzerdefiniertem Code: Generieren von partiellen Klassen.
Für Code, der Sie darüber hinaus manuell an den generierten Code schreiben können. Es ist ungewöhnlich, dass ein Code-Generierung-Schema in der Lage, alle möglichen Variationen berücksichtigen, die auftreten können. Aus diesem Grund sollten Sie erwarten, hinzuzufügen oder einen Teil des generierten Codes zu überschreiben. Die generierten Materials steht in einer .NET-Sprache wie z. B. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], zwei Strategien sind besonders nützlich:

- Die generierten Klassen sollten partiell sein. Dadurch können Sie zum Hinzufügen von Inhalt an den generierten Code.

- Klassen sollten paarweise auf – eine Vererbung von einem anderen generiert werden. Die Basisklasse muss alle generierten Methoden und Eigenschaften enthalten, und die abgeleitete Klasse sollte nur die Konstruktoren enthalten. Dadurch wird Ihre handgeschriebenem Code, um die generierten Methoden überschreiben.

  In anderen generierten Sprachen wie z. B. XML, verwenden die `<#@include#>` Direktive, um einfache Kombinationen von Hand geschriebene und generierten Inhalt zu erstellen. In komplexeren Fällen müssen Sie möglicherweise ein Nachverarbeitungsschritt zu schreiben, die die generierte Datei mit Hand geschriebene Dateien kombiniert.

  Häufige Material in Include-Dateien zu verschieben oder Laufzeitvorlagen, um zu vermeiden wiederholen ähnliche Blöcke von Text und Code in mehreren Vorlagen, verwenden Sie die `<#@ include #>` Richtlinie. Weitere Informationen finden Sie unter [T4-Include-Direktive](../modeling/t4-include-directive.md).

  Sie können auch die Laufzeit-Textvorlagen in einem separaten Projekt erstellen, und rufen sie dann aus der Vorlage zur Entwurfszeit. Verwenden Sie hierzu die `<#@ assembly #>` Richtlinie den Zugriff auf die separaten Projekt. Beispiele finden Sie in ["Vererbung in Textvorlagen" im Blog von Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

  Sollten Sie große Datenblöcke des Codes in eine separate Assembly verschieben.
  Wenn Sie große Code- und Klassenfunktionsblöcken verfügen, kann es hilfreich sein, Teile dieses Codes in Methoden zu verschieben, die Sie in einem separaten Projekt kompilieren. Sie können die `<#@ assembly #>` Richtlinie den Zugriff auf den Code in der Vorlage. Weitere Informationen finden Sie unter [T4-Assemblydirektive](../modeling/t4-assembly-directive.md).

  Sie können die Methoden in einer abstrakten Klasse einfügen, die die Vorlage erben kann. Die abstrakte Klasse erben muss <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Weitere Informationen finden Sie unter [T4-Vorlagenanweisung](../modeling/t4-template-directive.md).

  Generieren von Code, nicht Konfiguration Dateien eine Methode zum Schreiben einer Variablen Anwendung generische Programmcode schreiben, die eine Konfigurationsdatei akzeptiert. Eine Anwendung, die auf diese Weise geschrieben ist sehr flexibel und kann neu konfiguriert werden, wenn die geschäftsanforderungen ändern, ohne die Anwendung neu zu erstellen. Ein Nachteil dieses Ansatzes ist jedoch, dass die Anwendung nicht so gut wie eine spezifische Anwendung ausgeführt werden. Darüber hinaus werden die Programmcode schwieriger zu lesen und zu verwalten, teilweise daran, dass es immer hat für den Umgang mit der meisten generischen Typen.

  Im Gegensatz dazu kann eine Anwendung, deren Variablen Teile vor der Kompilierung generiert werden, stark typisiert werden. Dies macht es viel einfacher und zuverlässiger handgeschriebenem Code schreiben, und integrieren Sie sie in der generierten Teile dieser Software.

  Um alle Vorteile der codegenerierung zu erhalten, versuchen Sie, generieren Programmcode anstelle von Konfigurationsdateien.

  Verwenden Sie ein Ordner generierter Code platzieren Sie die Vorlagen und die generierten Dateien in einem Projektordner mit dem Namen **generierten Code**, damit es deaktivieren, dass diese Dateien nicht sind, die direkt bearbeitet werden soll. Wenn Sie benutzerdefinierten Code überschrieben oder hinzugefügt werden, auf die generierten Klassen erstellen, speichern Sie diese Klassen in einem Ordner mit dem Namen **benutzerdefinierten Code**. Die Struktur von einem typischen Projekt sieht folgendermaßen aus:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Richtlinien für die Laufzeit (vorverarbeiteten) T4-Vorlagen
 Verschieben von allgemeinem Material in geerbten Vorlagen können Sie Vererbung, Methoden und Textblöcke zwischen T4-Textvorlagen freizugeben. Weitere Informationen finden Sie unter [T4-Vorlagenanweisung](../modeling/t4-template-directive.md).

 Sie können auch Includedateien, die Laufzeit-Vorlagen haben.

 Verschieben Sie umfangreiche Codetexte in eine partielle Klasse.
Jede Laufzeitvorlage generiert eine partielle Klassendefinition, die den gleichen Namen wie die Vorlage hat. Sie können eine Codedatei schreiben, die einer anderen partiellen Definition der Klasse enthält. Sie können die Methoden, Felder und Konstruktoren auf die Klasse auf diese Weise hinzufügen. Diese Elemente können über die Codeblöcke in der Vorlage aufgerufen werden.

 Ein Vorteil besteht hierbei ist, dass der Code einfacher zu schreiben, da IntelliSense zur Verfügung steht. Darüber hinaus können Sie eine bessere Trennung zwischen der Präsentations- und die zugrunde liegende Logik erreichen.

 Z. B. in **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 In **MyReportText-Methods.cs**:

 `private string ComputeTotal() { ... }`

 Zulassen von benutzerdefiniertem Code: Bereitstellen von Erweiterungspunkten ggf. Generieren von virtuelle Methoden in \<#+ Klassenfunktion blockiert #>. Dadurch wird eine einzelne Vorlage, die in vielen Kontexten ohne Änderung verwendet werden. Anstatt die Vorlage ändern, können Sie eine abgeleitete Klasse erstellen, die die minimale zusätzliche Logik bereitstellt. Die abgeleitete Klasse kann entweder regulären Code, oder es kann eine Laufzeitvorlage sein.

 Z. B. in "MyStandardRunTimeTemplate.tt":

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
 Separate Sammeln von Daten aus der textgenerierung versuchen Sie, mischen Sie Berechnungen und Textblöcke. Verwenden Sie in jeder Textvorlage, die erste \<#-Codeblock #> zum Festlegen von Variablen und komplexe Berechnungen ausführen. Aus der ersten TextBlock ans Ende der Vorlage oder die erste \<#+ Klassenfunktion blockieren #>, vermeiden Sie lange Ausdrücke und Vermeiden von Schleifen und Bedingungen, wenn sie die Textblöcke enthalten. Diese Vorgehensweise erleichtert die Vorlage zu lesen und zu verwalten.

 Verwenden Sie keine `.tt` sind Dateien verwenden Sie eine andere Dateinamenerweiterung wie `.ttinclude` nach Includedateien. Verwendung `.tt` nur für Dateien, die Sie möchten wie Laufzeit oder Entwurfszeit-Textvorlagen verarbeitet. In einigen Fällen erkennt Visual Studio `.tt` -Dateien und deren Eigenschaften für die Verarbeitung automatisch festgelegt.

 Starten Sie jede Vorlage als feste Prototyp.
Schreiben Sie ein Beispiel für den Code oder Text, den Sie verwenden möchten, generieren, und stellen Sie sicher, dass er korrekt ist. Ändern Sie ihre Erweiterung in TT und inkrementell fügen Sie Code, den Inhalt lesen Sie das Modell ändert.

 Erwägen Sie typisierte Modelle.
Obwohl Sie ein XML-Index oder Datenbank-Schema für die Modelle erstellen können, kann es hilfreich sein, erstellen eine domänenspezifische Sprache (DSL) sein. Eine DSL hat den Vorteil, dass es sich um eine Klasse zur Darstellung von jedem Knoten im Schema und Eigenschaften, die die Attribute darstellen generiert. Dies bedeutet, dass Sie in Bezug auf das Geschäftsmodell programmieren können. Zum Beispiel:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Erwägen Sie die Verwendung von Diagrammen für die Modelle.
Viele Modelle sind am effektivsten angezeigt und verwaltet werden als Texttabellen, insbesondere dann, wenn sie sehr groß sind.

 Allerdings für einige Arten von geschäftsanforderungen, es ist wichtig, um komplexe Sätze von Beziehungen und Workflows zu verdeutlichen, und Diagrammen werden das am besten geeignet Medium. Ein Vorteil eines Diagramms ist, dass es einfach, um mit Benutzern und anderen Projektbeteiligten zu besprechen. Generieren von Code aus einem Modell auf der Ebene der geschäftlichen Anforderungen, stellen Sie Ihren Code mehr Flexibilität bei Anforderungen geänderten.

 Sie können auch einen eigenen Typ des Diagramms als domänenspezifische Sprache (DSL) entwerfen. Code kann von UML- und DSLs generiert werden. Weitere Informationen finden Sie unter [analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Siehe auch

- [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)
