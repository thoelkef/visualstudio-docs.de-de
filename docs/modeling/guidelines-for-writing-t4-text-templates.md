---
title: "Richtlinien für das Verfassen von T4-Textvorlagen | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 9
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 7d9dd7193455a625b0410eaca3b2bd243c109743
ms.lasthandoff: 02/22/2017

---
# <a name="guidelines-for-writing-t4-text-templates"></a>Richtlinien für das Verfassen von T4-Textvorlagen
Diese Richtlinien können hilfreich sein, wenn beim Generieren von Programmcode oder anderen Anwendungsressourcen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sie sind keine Regeln fest.  
  
## <a name="guidelines-for-design-time-t4-templates"></a>Richtlinien für die Entwurfszeit-T4-Vorlagen  
 Entwurfszeit-T4-Vorlagen sind Vorlagen, die generiert Code in Ihre [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt zur Entwurfszeit. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Generieren Sie Variable Teile der Anwendung.  
 Generieren von Code eignet sich am besten für die Aspekte der Anwendung, die möglicherweise während des Projekts wird ändern oder zwischen verschiedenen Versionen der Anwendung. Trennen Sie diese Variablen Teile von den weniger veränderlichen Teilen, damit Sie leichter feststellen können, was generiert werden muss. Wenn Ihre Anwendung eine Website bereitstellt, trennen Sie z. B. die Standardseite für die Funktionen von Logik, die die Navigationspfade von einer Seite in eine andere definiert.  
  
 Codieren Sie die Variablen Teile in eine oder mehrere Source-Modellen.  
 Ein Modell ist eine Datei oder Datenbank, die jeder Vorlage gelesen wird, um bestimmte Werte für Variable Teile des Codes zu erhalten, die generiert werden soll. Modelle können Datenbanken, XML-Dateien von Ihrem eigenen Design, Diagramme oder domänenspezifische Sprachen werden. Normalerweise wird ein Modell verwendet, um viele Dateien im Generieren einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. Jede Datei wird aus einer eigenen Vorlage generiert.  
  
 Sie können mehrere Modelle in einem Projekt verwenden. Sie können z. B. ein Modell für die Navigation zwischen Webseiten und ein separates Modell für das Layout der Seiten definieren.  
  
 Konzentrieren Sie das Modell auf die Bedürfnisse der Benutzer und das Vokabular, nicht auf Ihre Implementierung.  
 In einer Website-Anwendung würden Sie z. B. das Modell zum Verweisen auf Webseiten und Hyperlinks erwarten.  
  
 Im Idealfall, wählen Sie eine Präsentation, die die Art der Informationen am besten entspricht, das das Modell darstellt. Ein Modell der Navigationspfade über eine Website könnte z. B. ein Diagramm mit Feldern und Pfeilen sein.  
  
 Testen Sie den generierten Code.  
 Verwenden Sie manuelle oder automatisierte Tests, um sicherzustellen, dass der resultierende Code funktioniert, wie die Benutzer benötigen. Vermeiden Sie das Generieren von Tests aus dem gleichen Modell, in dem der Code generiert wird.  
  
 In einigen Fällen können allgemeine Tests direkt auf dem Modell durchgeführt werden. Sie könnten z. B. einen Test schreiben, der sicherstellt, dass jede Seite in der Website von der Navigation von einer anderen erreicht werden kann.  
  
 Zulassen von benutzerdefiniertem Code: Generieren von partiellen Klassen.  
 Zulassen von Code, die Sie von hand darüber hinaus an den generierten Code zu schreiben. Es ist ungewöhnlich, dass ein Code Generation Schema in der Lage, alle möglichen Variationen berücksichtigen, die auftreten können. Aus diesem Grund sollten Sie erwarten, hinzufügen oder einen Teil des generierten Codes zu überschreiben. In dem die generierten Materials ist in einer wie z. B. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], zwei Strategien sind besonders nützlich:  
  
-   Die generierten Klassen sollten partiell sein. Dadurch können Sie Inhalt an den generierten Code hinzuzufügen.  
  
-   Klassen, die in Paaren, einen erben von der anderen generiert werden soll. Die Basisklasse sollte alle generierten Methoden und Eigenschaften enthalten, und die abgeleitete Klasse sollte nur die Konstruktoren enthalten. Dadurch Ihre Hand geschriebene Code generierte Methoden überschreiben.  
  
 Verwenden Sie in anderen generierten Sprachen wie z. B. XML, die `<#@include#>` Direktive, um einfache Kombinationen von Hand geschriebene und generierten Inhalten zu erstellen. In komplexeren Fällen müssen Sie möglicherweise einen Nachverarbeitungsschritt schreiben, die die generierte Datei mit Hand geschriebene Dateien kombiniert.  
  
 Verschieben von allgemeinem Material in Include-Dateien oder Laufzeit-Vorlagen  
 Um wiederkehrende ähnliche Blöcke von Text und Code in mehreren Vorlagen zu vermeiden, verwenden Sie die `<#@ include #>` Richtlinie. Weitere Informationen finden Sie unter [T4-Include-Direktive](../modeling/t4-include-directive.md).  
  
 Sie können auch zur Laufzeit Textvorlagen in einem separaten Projekt erstellen, und nennen Sie diese aus der Vorlage zur Entwurfszeit. Verwenden Sie hierzu die `<#@ assembly #>` Direktive, um das separate Projekt zuzugreifen. Beispiele finden Sie unter ["Vererbung in Textvorlagen" im Blog von Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
 Erwägen Sie große Datenblöcke des Codes in einer separaten Assembly.  
 Wenn Sie große Code- und Klassenfunktionsblöcke verfügen, kann es hilfreich sein, die Teil des Codes in Methoden zu verschieben, die Sie in einem separaten Projekt kompilieren. Sie können die `<#@ assembly #>` Richtlinie den Zugriff auf den Code in der Vorlage. Weitere Informationen finden Sie unter [T4-Assemblydirektive](../modeling/t4-assembly-directive.md).  
  
 Sie können die Methoden in einer abstrakten Klasse einfügen, die die Vorlage erben kann. Die abstrakte Klasse muss <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> erben Weitere Informationen finden Sie unter [T4-Vorlagendirektive](../modeling/t4-template-directive.md).  
  
 Generieren von Code, der keine Konfigurationsdateien  
 Eine Methode zum Schreiben einer Variablen Anwendung besteht darin generischen Programmcode schreiben, der eine Konfigurationsdatei akzeptiert. Eine Anwendung, die auf diese Weise geschrieben ist sehr flexibel und kann neu konfiguriert werden, wenn die geschäftlichen Anforderungen zu ändern, ohne das Neuerstellen der Anwendung. Ein Nachteil dieses Ansatzes ist jedoch, dass die Anwendung nicht so gut wie eine spezifische Anwendung ausgeführt wird. Der Programmcode wird außerdem schwieriger zu lesen und zu verwalten sein, teilweise verwendet werden, da sie immer für den Umgang mit der meisten generischen Typen verfügt.  
  
 Im Gegensatz dazu kann eine Anwendung, deren Variable Teile vor der Kompilierung generiert werden, stark typisiert werden. Dies macht es viel einfacher und zuverlässiger Hand geschriebene Code schreiben und integrieren sie in der generierten Teile der Software.  
  
 Um alle Vorteile der Generierung von Code zu erhalten, versuchen Sie, Programmcode anstelle von Konfigurationsdateien generieren.  
  
 Verwenden Sie einen Ordner für generierten Code  
 Setzen Sie die Vorlagen und die generierten Dateien in einem Projektordner mit dem Namen **generierten Code**, damit es deaktivieren, dass diese nicht Dateien, die nicht direkt bearbeitet werden soll. Bei der Erstellung benutzerdefinierten Codes zum Überschreiben oder zu den generierten Klassen hinzufügen, speichern Sie diese Klassen in einem Ordner mit dem Namen **benutzerdefinierten Code**. Die Struktur von einem typischen Projekt sieht folgendermaßen aus:  
  
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
 Verschieben von allgemeinem Material in geerbte Vorlagen  
 Sie können Vererbung verwenden, Methoden und Textblöcke zwischen T4-Textvorlagen freigeben. Weitere Informationen finden Sie unter [T4-Vorlagendirektive](../modeling/t4-template-directive.md).  
  
 Sie können auch Dateien, die über Laufzeitvorlagen verfügen.  
  
 Verschieben Sie umfangreiche Codetexte in einer partiellen Klasse.  
 Jede Laufzeitvorlage generiert eine partielle Klassendefinition, die den gleichen Namen wie die Vorlage. Sie können eine Codedatei schreiben, die eine andere partielle Definition der Klasse enthält. Sie können Methoden, Felder und Konstruktoren der Klasse auf diese Weise hinzufügen. Diese Member können von den Codeblöcken in der Vorlage aufgerufen werden.  
  
 Ein Vorteil dieser Vorgehensweise ist, dass der Code einfacher zu schreiben, da IntelliSense verfügbar ist. Darüber hinaus können Sie eine bessere Trennung zwischen der Präsentations- und die zugrunde liegende Logik erzielen.  
  
 Wenn beispielsweise in **MyReportText.tt**:  
  
 `The total is: <#= ComputeTotal() #>`  
  
 In **MyReportText Methods.cs**:  
  
 `private string ComputeTotal() { ... }`  
  
 Zulassen von benutzerdefiniertem Code: Bereitstellen von Erweiterungspunkten  
 Erwägen Sie die Generierung von virtueller Methoden in \<#+ Klassenfunktion blockiert #>. Dadurch wird eine einzelne Vorlage in vielen Kontexten ohne Änderung verwendet werden. Anstelle der Vorlage ändern, können Sie eine abgeleitete Klasse erstellen, die die minimale zusätzliche Logik bereitstellt. Die abgeleitete Klasse kann entweder um regulären Code oder eine Vorlage zur Laufzeit möglich.  
  
 Wenn beispielsweise in "MyStandardRunTimeTemplate.tt":  
  
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
 Sammeln von Daten aus Text-Generierung trennen  
 Versuchen Sie, die Berechnung und Textblöcke vermischen zu vermeiden. Verwenden Sie in jeder Textvorlage die erste \<# Codeblock #> zum Festlegen von Variablen und komplexe Berechnungen ausführen. Aus dem ersten TextBlock zum Ende der Vorlage oder die erste \<#+ Klassenfunktion blockieren #>, vermeiden Sie lange Ausdrücke und Vermeiden von Schleifen und Bedingungen, wenn sie die Textblöcke enthalten. Diese Vorgehensweise erleichtert die Vorlage zu lesen und zu verwalten.  
  
 Verwenden Sie keine `.tt` von Include-Dateien  
 Verwenden Sie eine andere Erweiterung wie `.ttinclude` nach Includedateien. Verwendung `.tt` nur für Dateien, die Sie möchten als zur Laufzeit oder Entwurfszeit Textvorlagen verarbeitet. In einigen Fällen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erkennt `.tt` -Dateien und deren Eigenschaften für die Verarbeitung automatisch festgelegt.  
  
 Beginnen Sie jede Vorlage mit einem festen Prototyp.  
 Schreiben Sie ein Beispiel des Codes oder der Text, der zu generieren, und stellen Sie sicher, dass er korrekt ist. Ändern Sie die Erweiterung in .tt, und fügen Sie inkrementell Code, der den Inhalt durch Lesen des Modells ändert.  
  
 Erwägen Sie typisierte Modelle.  
 Obwohl Sie eine XML- oder Datenbankschema für die Modelle erstellen können, kann es hilfreich sein, eine domänenspezifische Sprache (DSL) zu erstellen sein. Eine domänenspezifische Sprache hat den Vorteil, dass eine Klasse zum Darstellen von jedem Knoten im Schema und Eigenschaften, um die Attribute darstellen generiert. Dies bedeutet, dass Sie in Bezug auf das Geschäftsmodell programmieren können. Zum Beispiel:  
  
```  
Team Members:  
<# foreach (Person p in team.Members)   
 { #>   
    <#= p.Name #>   
<# } #>  
```  
  
 Verwenden Sie ggf. Diagramme für die Modelle.  
 Viele Modelle sind am effektivsten präsentiert und einfach als Texttabellen verwaltet werden, insbesondere dann, wenn sie sehr groß sind.  
  
 Allerdings für einige Arten von geschäftsanforderungen, es ist wichtig, komplexe Sätze von Beziehungen und Workflows zu erläutern und Diagramme sind die am besten geeignet Mittel. Ein Vorteil eines Diagramms ist, dass es problemlos mit Benutzern und anderen Projektbeteiligten besprochen werden. Generieren von Code aus einem Modell auf der Ebene der geschäftlichen Anforderungen, stellen Sie Ihren Code flexibler bei Anforderungen geänderten.  
  
 Sie können auch einen eigenen Typ des Diagramms als domänenspezifische Sprache (DSL) entwerfen. Code kann von UML- und DSLs generiert werden. Weitere Informationen finden Sie unter [Architektur modellieren und Analysieren von](../modeling/analyze-and-model-your-architecture.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)   
 [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)

