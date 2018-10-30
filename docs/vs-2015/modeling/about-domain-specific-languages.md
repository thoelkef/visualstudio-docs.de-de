---
title: Informationen zu domänenspezifischen Sprachen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6cddf51705758d046ab66319d6ac6295f3a4b057
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894520"
---
# <a name="about-domain-specific-languages"></a>Informationen zu domänenspezifischen Sprachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Gegensatz zu einer Sprache wie c# oder UML-eine domänenspezifische Sprache (DSL) soll Anweisungen in einer bestimmten Problembereich oder Domäne express.  
  
 Well-Known DSLs sind reguläre Ausdrücke und SQL. Jede DSL ist viel besser als eine Sprache zum Beschreiben der Vorgänge für Zeichenfolgen oder eine Datenbank, sondern eher schlechter zum Beschreiben von Ideen, die außerhalb der eigenen Bereichs liegen. Einzelne Branchen können auch ihre eigenen DSLs. Z. B. in der Telekommunikationsbranche rufen Sie Beschreibung an auf, die Sprachen, geben die Sequenz der Status in einen Telefonanruf an, und übertragen in der Luft Branche weit verbreitet ist ein Standard, die DSL mit der Flug Buchungen beschrieben werden.  
  
 Ihr Unternehmen und Ihr Projekt betreffen auch spezielle Sätze von Konzepten, die mit einer DSL beschrieben werden können. Beispielsweise können Sie eine DSL für eine dieser Anwendungen definieren:  
  
- Planen der Navigationspfade auf einer Website.  
  
- Schaltpläne für elektronische Komponenten.  
  
- Netzwerke von Fließbändern und gepäckbeförderungsausrüstung für einem Flughafen.  
  
  Beim Entwerfen einer DSL, die Sie definieren eine *Domänenklasse* für die einzelnen wichtiger Konzepte, die in der Domäne, z. B. eine Webseite, Lamp oder Flughafen-Check-in –. Sie definieren *domänenbeziehungen* wie Links, über das Netzwerk oder ein Fließband, um die Konzepte miteinander zu verknüpfen.  
  
  Erstellen von Benutzern Ihrer DSL *Modelle.* Modelle sind *Instanzen* der DSL. Beschreiben sie beispielsweise eine bestimmte Website oder die Verknüpfung der ein bestimmtes Gerät oder das System in einem bestimmten Flughafen für die Gepäckbeförderung.  
  
  Ihre Benutzer können ein Modell als Diagramm oder ein Windows-Formular anzeigen. Modelle können auch angezeigt werden als XML, wie sie gespeichert werden. Wenn Sie eine DSL definieren, definieren Sie, wie die Instanzen der einzelnen Domänenklasse und die Beziehungen auf dem Bildschirm des Benutzers angezeigt werden. Eine typische DSL wird als eine Auflistung von Symbolen oder Rechtecke, die Verbindung durch Pfeile angezeigt.  
  
  Die folgende Abbildung zeigt ein kleines Modell in einer DSL DSL an:  
  
  ![Tudor-Stammstrukturmodell](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>Was können Sie mit DSLs tun.  
 Eine typische Anwendung einer DSL ist Programmcode oder andere Artefakte generieren. Wenn Sie Ihre DSL definiert haben, können Sie definieren *Textvorlagen* , lesen Sie ein Modell für die DSL, und Generieren von Textdateien.  
  
 Beispielsweise könnten Sie Vorlagen schreiben, die einen Flughafen-Plan und Teil der Software für Gepäck verarbeitet werden, sowie einige der Benutzerdokumente, die beschreiben, den Plan zu generieren.  
  
 Wenn Sie eine DSL definiert haben, können Sie es für andere Benutzer verteilen, die sie auf ihren eigenen Computern installieren können. Es können Benutzer Ihrer DSL erstellen und Bearbeiten von Modellen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Sie können auch Befehle im Menü definieren, und andere Tools, die Benutzern helfen bearbeiten Sie die DSL, validierungseinschränkungen, um sicherzustellen, dass die DSL ordnungsgemäß verwendet wird, und Elementvorlagen, die Benutzern helfen, neue Instanzen erstellen. Sie können eine oder mehrere DSLs mit ihren Tools und andere umschließen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen als integrierte-Paket.  
  
 In der Regel ist eine domänenspezifische Sprache erstellt, wenn ein Entwicklungsteam ist ähnlich wie Code für mehrere Produkte schreiben. Beispielsweise kann ein Unternehmen, das sich auf Gepäckabfertigungssysteme spezialisiert hat Gepäck nachverfolgen DSL definieren, aus der sie einen Teil des Codes für jede Installation generieren können. Die Vorteile der DSL sind, dass sie, dass der daraus generierte Code zuverlässig ist und das System schnell aktualisiert werden kann, wenn der Kunden Anforderungen ändern, von ihren Kunden, verstanden werden können.  
  
 [!INCLUDE[dsl](../includes/dsl-md.md)] ermöglicht Ihnen das Erstellen einer domänenspezifischen Sprache, die Ihre eigenen grafischen Designer und Ihre eigenen Diagramm-Notation aufweist, und klicken Sie dann mit der die Sprache entsprechenden Quellcode für jedes Projekt generiert.  
  
## <a name="domain-specific-development"></a>Domain-Specific-Entwicklung  
 Domänenspezifische Entwicklung ist der Prozess zum Identifizieren der Teile von Anwendungen, die modelliert werden können, indem mithilfe einer domänenspezifischen Sprache, und klicken Sie dann erstellen die Sprache und für die Anwendungsentwickler bereitstellen. Die Entwickler verwenden die domänenspezifische Sprache zum Erstellen von Modellen, die für ihre Anwendungen spezifisch sind, verwenden Sie die Modelle zum Generieren von Quellcode und verwenden den Quellcode klicken Sie dann die Anwendungen zu entwickeln.  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekte der Entwicklung von Grafischen domänenspezifische  
 Eine grafische einer domänenspezifischen Sprache muss es sich um die folgenden Funktionen enthalten:  
  
-   Notation  
  
-   Domänenmodell  
  
-   Artefakt-Generierung  
  
-   Serialisierung  
  
-   Integration in Visual Studio  
  
### <a name="notation"></a>Notation  
 Eine domänenspezifische Sprache muss es sich um einen relativ kleinen Satz von Elementen verfügen, leicht definiert und erweitert, um die Darstellung einer domänenspezifischen-Konstrukte werden können. Eine Notation besteht aus Formen, die die Elemente darstellen, und Connectors, die die Beziehungen zwischen Elementen, die auf einer Oberfläche grafisches Diagramm darstellen. In [!INCLUDE[dsl](../includes/dsl-md.md)], die Formen erweitert und verbessert, um die Elemente der domänenspezifischen Sprache darstellen werden können.  
  
### <a name="domain-model"></a>Domänenmodell  
 Eine domänenspezifische Sprache muss den Satz von Elementen und die Beziehungen zwischen ihnen in eine kohärente Grammatik kombinieren. Sie müssen außerdem definieren, ob Kombinationen von Elementen und Beziehungen gültig sind. Beispielsweise verhindern Programmiersprachen, in der Regel zirkuläre Vererbung, in dem eine Klasse von einer Sekunde-Klasse abgeleitet ist, und die zweite Klasse von der ersten Klasse abgeleitet ist. Einschränkungen können auch verwendet werden, um Geschäftslogik auszudrücken, z. B. nicht eine Person ein abhängiges Element selbst. [!INCLUDE[dsl](../includes/dsl-md.md)] verwendet von Einschränkungen, die Arten von Einschränkungen auszudrücken, die meisten domänenspezifischen Sprachen erforderlich.  
  
### <a name="artifact-generation"></a>Artefakt-Generierung  
 Eine der wichtigsten Gründe einer domänenspezifischen Sprache ist ein Artefakt, z. B. Quellcode, eine XML-Datei oder einige andere brauchbare Daten zu generieren. In der Regel bedeutet eine Änderung im Modell eine Änderung im Artefakt an. Sie können [!INCLUDE[dsl](../includes/dsl-md.md)] um Elemente zu generieren und Sie diese erneut generieren, wenn Sie das Modell ändern.  
  
### <a name="serialization"></a>Serialisierung  
 Eine domänenspezifische Sprache muss in irgendeiner Form beibehalten werden, die bearbeitet, gespeichert, geschlossen und erneut geladen werden können. [!INCLUDE[dsl](../includes/dsl-md.md)] verwendet eine XML-Format, mit dem Sie definieren und anpassen, wie Ihre Domain-Specific Languge serialisiert oder beibehalten wird.  
  
### <a name="integration-with-visual-studio"></a>Integration in Visual Studio  
 Da [!INCLUDE[dsl](../includes/dsl-md.md)] gehostet wird, im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], viele erweitert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Fenster und Steuerelemente. Außerdem können Sie das Verhalten der Befehle im Menü Toolboxelemente und andere Elemente der Benutzeroberfläche anpassen.  
  
 Sie können auch eine Modellbusadapter für Ihre einer domänenspezifischen Sprache erstellen. Dieser Adapter können Sie mit Verweis ein Modell und Elementen in einem Modell und können, die Sie Code schreiben, können den Zugriff auf und Aktualisieren einer Instanz der DSL. Sie können mithilfe des leistungsstarken Modellbus-Mechanismus zu verwenden, schreiben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterungen, die mit mehreren Modellen arbeiten. Sie können auch die eigenständige Anwendungen schreiben, die mit Modellen arbeiten. Weitere Informationen finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Vorteile der Entwicklung von domänenspezifischen  
 Eine domänenspezifische Sprache, bieten die folgenden Vorteile:  
  
-   Enthält die Konstrukte, die den Problembereich genau entsprechen.  
  
     Im Gegensatz zu den allgemeinen Sprachen besteht aus eine domänenspezifischen Sprache von Elementen und Beziehungen, die direkt auf die Logik der den Problembereich darstellen. Beispielsweise muss eine Versicherungspolice-Anwendung Elemente für Richtlinien und die Ansprüche enthalten. Eine domänenspezifische Sprache erleichtert das Entwerfen der Anwendung, und suchen und beheben Sie Fehler Logik.  
  
-   Können nicht-Entwickler und Personen, die nicht die Domäne den Gesamtentwurf verstehen kennen.  
  
     Mit einer grafischen einer domänenspezifischen Sprache, können Sie eine visuelle Darstellung der Domäne erstellen, damit nicht-Entwickler ganz einfach das Design der Anwendung nachvollziehen können.  
  
-   Ist es einfacher, einen Prototyp der endgültigen Anwendung zu erstellen.  
  
     Entwickler können den Code verwenden, den ihr Modell generiert wird, um einen prototypenanwendung zu erstellen, die sie für Clients anzeigen können.  
  
## <a name="the-process-of-domain-specific-development"></a>Der Prozess der Entwicklung von domänenspezifischen  
 Die meisten Softwareentwicklungsteams, die einer domänenspezifischen Sprachen verwenden, gehen Sie zum Erstellen und verwenden ihre Modelle:  
  
-   Das Team unterscheidet es sich um die Variablen Teile der Domäne aus den Teilen, die sich nie ändern.  
  
-   Die Entwickler Schreiben von Code für die feste Bestandteile und Erweiterungspunkte für die Variablen Teile lassen.  
  
-   Der Entwicklungsleiter für die Software oder der Architekt erstellt eine domänenspezifische Sprache, die die Entwurfsmuster festen Teile der Domäne und die Erweiterungspunkte für die Variablen Teile umfasst.  
  
-   Der Entwicklungsleiter für die Software oder der Architekt stellt die Entwickler von den verschiedenen Anwendungen, die das Team erstellt die Domain-Specific Languge bereit.  
  
-   Jeder Entwickler erstellt ein Modell, das für die jeweilige Anwendung gilt.



