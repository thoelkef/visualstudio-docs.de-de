---
title: "Informationen zu den domänenspezifische Sprachen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: "26"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7bdd5f6f9561e3479d173a1e182ffa07649bc776
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="about-domain-specific-languages"></a>Informationen zu domänenspezifischen Sprachen
Im Gegensatz zu einer allgemeinen Sprache wie c# oder UML-dient eine domänenspezifische Sprache (DSL) express Anweisungen in einer bestimmten Problembereich oder Domäne.  
  
 Well-Known konzentriert sind reguläre Ausdrücke und SQL. Jede DSL ist wesentlich besser als eine allgemeine Sprache zum Beschreiben von Operationen Textzeichenfolgen oder einer Datenbank, sondern eher schlechter zum Beschreiben von Ideen, die außerhalb ihres eigenen Bereichs liegen. Einzelne Branchen können auch ihre eigenen konzentriert. Beispielsweise in der Telekommunikationsbranche rufen Sie Beschreibung an, die Sprachen häufig verwendet werden, um die Sequenz von Zuständen in einen Telefonanruf angeben, und in der Luft Reisen Branche eine Standard-DSL mit der Flug ig beschrieben werden.  
  
 Ihr Unternehmen und Ihrem Projekt verarbeiten auch spezielle Sätze von Konzepten, die mit einem DSL beschrieben werden können. Sie können z. B. eine DSL für eine dieser Anwendungen definieren:  
  
-   Planen der Navigationspfade auf einer Website.  
  
-   Schaltpläne für elektronische Komponenten.  
  
-   Netzwerke von Fließbändern und gepäckbeförderungsausrüstung für in einem Flughafen.  
  
 Wenn Sie eine DSL entwerfen, definieren Sie eine *Domänenklasse* aller wichtiger Konzepte, die in der Domäne, z. B. eine Webseite, Lamp oder Flughafen Einchecken-Schalters. Sie definieren *domänenbeziehungen* z. B. Hyperlink, über das Netzwerk oder ein Förderband transportiert die Konzepte miteinander verknüpfen.  
  
 Erstellen von Benutzern für Ihre DSL *Modelle.* Modelle sind *Instanzen* der DSL. Beschreiben sie beispielsweise eine bestimmte Website oder dem Verknüpfen eines ein bestimmtes Gerät oder das System in einem bestimmten Flughafen für die Gepäckbeförderung.  
  
 Ihre Benutzer können ein Modell als Diagramm oder als ein Windows Form anzeigen. Modelle können auch angezeigt werden als XML, also wie diese gespeichert sind. Wenn Sie eine DSL definieren, definieren Sie, wie die Instanzen der einzelnen Domänenklasse und jede Beziehung auf dem Bildschirm des Benutzers angezeigt werden. Eine typische DSL wird als eine Auflistung von Symbolen oder Rechtecke, die durch Pfeile verbunden angezeigt.  
  
 Die folgende Abbildung zeigt ein kleines Modell, in eine Verbindungskabel als Diagramm DSL:  
  
 ![Tudor-Stammbaummodell](../modeling/media/tudor_familytreemodel.png "Tudor_FamilyTreeModel")  
  
## <a name="what-you-can-do-with-dsls"></a>Was können Sie mit konzentriert tun.  
 Eine typische Anwendung eine DSL ist Programmcode oder andere Artefakte generieren. Wenn Sie mit der DSL definieren, können Sie definieren *Textvorlagen* , lesen Sie ein Modell für die DSL und Generieren von Textdateien.  
  
 Beispielsweise konnte Sie Vorlagen schreiben, die nehmen einen Plan Flughafen und Teil der Software für die Gepäckbeförderung sowie einige der Benutzerdokumente, die beschreiben, den Plan zu generieren.  
  
 Wenn Sie eine DSL definiert haben, können Sie ihn an andere Benutzer verteilen, die es auf ihren Computern installieren können. Benutzer von der DSL erstellen und Bearbeiten von Modellen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Außerdem können Menübefehle und andere Tools, mit denen Benutzer Bearbeiten der DSL validierungseinschränkungen, um sicherzustellen, dass der DSL ordnungsgemäß verwendet wird, und Elementvorlagen, mit denen Benutzer neue Instanzen erstellen. Sie können eine oder mehrere konzentriert mit ihren Tools und andere umschließen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen als integrierte-Paket.  
  
 In der Regel wird eine domänenspezifische Sprache erstellt, wenn ein Entwicklungsteam hat ähnlichen Code für verschiedene Produkte schreiben. Ein Unternehmen, die Systeme für die Gepäckbeförderung spezialisiert kann z. B. eine Gepäck nachverfolgen DSL definieren, aus der sie Teil des Codes für jede Installation generieren können. Die Vorteile der DSL sind, dass es, dass von ihm generierte Code zuverlässig ist und das System schnell aktualisiert werden kann, wenn die Anforderungen der Kunden ändern von ihren Kunden und verstanden werden können.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]können Sie erstellen eine domänenspezifische Sprache, die Ihre eigenen Grafikdesigner und eigene Notation Diagramm verfügt, und klicken Sie dann die Sprache verwenden, um die entsprechenden Quellcode für jedes Projekt generieren.  
  
## <a name="domain-specific-development"></a>Domänenspezifische Entwicklung  
 Domänenspezifische Entwicklung ist der Prozess der Identifizierung der Bestandteile Ihrer Anwendungen, die modelliert werden können, mithilfe einer domänenspezifischen Sprache, und erstellen die Sprache und auf die Anwendungsentwickler bereitgestellt. Der Entwickler mithilfe einer domänenspezifischen Sprache erstellen Modelle, die für ihre Anwendungen spezifisch sind, verwenden Sie die Modelle zum Generieren von Quellcode und verwenden Sie den Quellcode der Anwendungsentwicklung.  
  
## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekte bei der Entwicklung von Grafischen domänenspezifische  
 Eine grafische einer domänenspezifischen Sprache muss es sich um die folgenden Funktionen enthalten:  
  
-   Notation  
  
-   Domänenmodell  
  
-   Generierung des Artefakt  
  
-   Serialisierung  
  
-   Integration in Visual Studio  
  
### <a name="notation"></a>Notation  
 Eine domänenspezifische Sprache benötigen einen relativ kleinen Satz von Elementen, die problemlos definiert und zur Darstellung einer domänenspezifischen Konstrukte erweitert werden können. Eine Notation besteht aus Formen, die die Elemente darstellen, und Connectors, die die Beziehungen zwischen Elementen, auf einer Oberfläche grafisches Diagramm darstellen. In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], Formen verfeinert wird, um die Elemente einer domänenspezifischen Sprache darstellen und erweitert werden können.  
  
### <a name="domain-model"></a>Domänenmodell  
 Eine domänenspezifische Sprache muss die Gruppe von Elementen und die Beziehungen zwischen ihnen in eine kohärente Grammatik kombinieren. Sie müssen außerdem definieren, ob die gültigen Kombinationen aus Elementen und Beziehungen. Programmiersprachen verhindern beispielsweise in der Regel zirkulären Vererbung, in dem eine Klasse aus einer zweiten Klasse abgeleitet ist, und die zweite Klasse von der ersten Klasse abgeleitet ist. Einschränkungen können auch verwendet werden, um Geschäftslogik auszudrücken, z. B. darf nicht eine Person ein abhängiges Objekt von sich selbst sein. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]verwendet Integritätsregeln, die Arten von Beschränkungen auszudrücken, die am häufigsten domänenspezifische Sprachen erforderlich ist.  
  
### <a name="artifact-generation"></a>Generierung des Artefakt  
 Eine der Hauptverwendungszweck einer domänenspezifischen Sprache ist ein Artefakt, z. B. Quellcode, eine XML-Datei und einige andere verwendbaren Daten zu generieren. In der Regel bedeutet, dass eine Änderung im Modell eine Änderung im Elementspeicher. Sie können [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] um Elemente zu generieren und diese erneut zu generieren, wenn Sie das Modell ändern.  
  
### <a name="serialization"></a>Serialisierung  
 Eine domänenspezifische Sprache muss sich in irgendeiner Form beibehalten werden, die bearbeitet, gespeichert, geschlossen und erneut geladen werden können. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]verwendet eine XML-Format, mit dem Sie definieren und anpassen, wie Ihre einer domänenspezifischen Sprache serialisiert oder beibehalten werden.  
  
### <a name="integration-with-visual-studio"></a>Integration in Visual Studio  
 Da [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] gehostet wird, im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], erweitert viele [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows- und Steuerelemente. Außerdem können Sie das Verhalten der Menübefehle und Toolboxelemente andere Elemente der Benutzeroberfläche anpassen.  
  
 Sie können auch einen Hostbusadapter Modell für Ihre einer domänenspezifischen Sprache erstellen. Diese Adapter können Sie Verweis ein Modell und Elemente innerhalb eines Modells und können, die Sie Code schreiben, die Zugriff auf und aktualisieren Sie eine Instanz der DSL können. Sie können mithilfe der leistungsstarken ModelBus (Modellbus)-Mechanismus schreiben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen, die mit mehreren Modellen arbeiten. Sie können auch die eigenständige Anwendungen schreiben, die mit Modellen arbeiten. Weitere Informationen finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="benefits-of-domain-specific-development"></a>Vorteile der Domain-Specific-Entwicklung  
 Eine domänenspezifische Sprache, kann die folgenden Vorteile bieten:  
  
-   Enthält die Konstrukte, die das Problemfeld genau entsprechen.  
  
     Im Gegensatz zu allgemeinen Sprachen besteht aus eine domänenspezifischen Sprache Elementen und Beziehungen, die die Logik für das Problemfeld direkt darstellen. Beispielsweise muss eine Versicherung-Anwendung Elemente für Richtlinien und Ansprüche enthalten. Eine domänenspezifische Sprache erleichtert es, die Anwendung, und suchen und beheben Sie Fehler Logik entwerfen.  
  
-   Können nicht-Entwickler und Personen, die nicht die Domäne, die den Gesamtentwurf verstehen kennen.  
  
     Mithilfe einer grafischen einer domänenspezifischen Sprache können Sie eine visuelle Darstellung der Domäne erstellen, sodass nicht-Entwickler den Entwurf der Anwendung leicht verstanden werden können.  
  
-   Erleichtert es, einen Prototyp der endgültigen Anwendung zu erstellen.  
  
     Entwickler können den Code verwenden, den ihr Modell generiert wird, um einen Prototyp-Anwendung zu erstellen, die auf Clients angezeigt werden können.  
  
## <a name="the-process-of-domain-specific-development"></a>Der Prozess der Entwicklung einer domänenspezifischen  
 Schritte zum Erstellen und ihre Modelle verwenden die meisten Softwareentwicklungsteams, die domänenspezifische Sprachen verwenden:  
  
-   Das Team unterscheidet, der Variablenteile der Domäne aus den Teilen, die nie geändert werden.  
  
-   Die Entwickler schreiben Sie Code für die feste Teile und lassen Sie Erweiterungspunkte für die Variablen Teile.  
  
-   Der Entwicklungsleiter-Software oder der Architekt erstellt eine domänenspezifische Sprache, die das Entwurfsmuster der feste Bestandteile der Domäne und die Erweiterungspunkte für die Variablen Teile enthält.  
  
-   Der Entwicklungsleiter-Software oder der Architekt domänenspezifische Sprache, die auf den Entwicklern von den verschiedenen Clientanwendungen, die das Team erstellt bereitgestellt werden.  
  
-   Jeder Entwickler erstellt ein Modell, das für die jeweilige Anwendung gilt.