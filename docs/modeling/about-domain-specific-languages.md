---
title: "Informationen zu dom&#228;nenspezifischen Sprachen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache"
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 26
caps.handback.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Informationen zu dom&#228;nenspezifischen Sprachen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Anders als eine gemeinsame Sprache wie C\# oder UML, ist eine domänenspezifische Sprache \(DSL\) mit den Erklärungen ausdrücklichen ein bestimmtes Problem in der Domäne oder leer.  
  
 Bekanntes DSL enthält reguläre Ausdrücke und SQL.  Jede DSL ist wesentlich besser als eine gemeinsame Sprache zum Beschreiben von Operationen für Textzeichenfolgen oder einer Datenbank, sondern ein viel ungültiger zum Beschreiben von Ideen, die außerhalb sein eigener Bereich befinden.  Einzelne Wirtschaftszweige verfügen auch über ein eigenes DSL.  In der Telekommunikations industrie, sind Aufrufs beschreibungs Sprachen weit weitergegeben, die Folge von Zuständen in einem Telefonanruf anzugeben, und in der Luft DSL reisebranche wird ein Standardwert verwendet, um Flugbuchungen zu beschreiben.  
  
 Das Unternehmen und das Projekt arbeiten auch spezielle Sätze Konzepte mit einem DSL beschrieben werden konnten.  Sie können z. B. ein DSL für eine dieser Anwendungen definieren:  
  
-   Planen von Navigationspfaden in einer Website.  
  
-   Bauschaltpläne für elektronische Bauelemente.  
  
-   Netzwerken aus Förderbändern und Gepäckabfertigungs für einen arbeitsgeräten Flughafen.  
  
 Wenn Sie ein DSL gestalten, definieren Sie eine *Domänenklasse* für jedes wichtiger Konzepte in der Domäne, z. B. eine Webseite, eine Lampe oder einem abflugschalter Flughafen.  Sie definieren *Domänen\-Verhältnisse* wie Link, Kabel oder ein Förderband, um die Konzepte zu verknüpfen.  
  
 Benutzer des DSL *Modelle*erstellen *.* Modelle sind *Instanzen des* DSL.  Zum Beispiel wird sie eine bestimmte Website oder Verdrahtung eines bestimmten Geräts oder des Gepäckabfertigungs in einem bestimmten systems Flughafen.  
  
 Die Benutzer können ein Modell anzeigen, während ein Diagramm oder als Windows Form.  Modelle können auch als XML dargestellt werden, z. B. der sie gespeichert werden.  Wenn Sie ein DSL definieren, definieren Sie, wie die Instanzen jeder Domänenklasse und \- verhältnisses auf dem Bildschirm des Benutzers angezeigt werden.  Ein typisches DSL wird als Auflistung von Symbolen oder Rechtecken angezeigt, die durch Pfeile verbunden sind.  
  
 Die folgende Abbildung zeigt ein kleines in einem grafischen Modell angezeigt: DSL  
  
 ![Tudor&#45;Stammbaummodell](../modeling/media/tudor_familytreemodel.png "Tudor\_FamilyTreeModel")  
  
## Mögliche Aktionen mit DSL möglich ist  
 Eine typische Verwendung eines DSL ist, Programmcode oder andere Artefakte generieren.  Wenn Sie das DSL definieren, können Sie *Textvorlagen* definieren, die ein Modell des DSL lesen und Textdateien generieren.  
  
 Beispielsweise können Sie Vorlagen, die einen Flughafen plan übernehmen und Teil der Software für Gepäckabfertigung generieren, sowie einige der Benutzer Dokumente schreiben, die den Plan beschreiben.  
  
 Wenn Sie ein DSL definiert haben, können Sie sie an andere Benutzer verteilen, die auf ihren eigenen Computern installieren können.  Benutzer des DSL können Modelle in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]erstellen und bearbeiten.  
  
 Sie können Menübefehle und andere Tools, die Benutzern das DSL Hilfe zu bearbeiten, Validierungseinschränkungen sicherzustellen, dass das DSL ordnungsgemäß verwendet wird, und Elementvorlagen definieren, die Benutzern helfen, neue Instanzen zu erstellen.  Sie können eine oder mehrere DSL mit ihren Tools und anderen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen als integriertes Paket einschließen.  
  
 In der Regel wird eine domänenspezifische Sprache erstellt, wenn ein Entwicklungsteam ähnlichen Code für einige Produkte schreiben müssen.  Zum Beispiel könnte ein Unternehmen definiert, das in den Gepäckabfertigungs systemen spezialisiert, einen Gepäck Bildlaufziehleiste DSL, von denen sie ein Teil des Codes für jede Installation generieren können.  Die Vorteile des DSL sind, dass sie ihre Kunden verstanden werden kann, dass der Code, der von ihm generiert wird, und zuverlässig ist und dass das System schnell aktualisiert werden kann, wenn die Anforderungen der Kunden ändern.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] können Sie eine domänenspezifische Sprache erstellen, die verfügt, grafischen Designer verfügen, Diagramm und schreibweise besitzen, und verwendet dann die Sprache, um entsprechenden Quellcode für jedes Projekt zu generieren.  
  
## Domänenspezifische Entwicklung  
 Domänenspezifische Entwicklung ist der Prozess der Identifizierung der Teile der Anwendungen, die erstellt werden können, indem eine domänenspezifische Sprache verwendet, und die Sprache erstellen und diese dann auf Bereitstellen. Anwendungsentwickler  Die Entwickler verwenden die domänenspezifische Sprache, um Modelle zu erstellen, die mit ihren Anwendungen vorgesehen sind, verwenden die Modelle zum Generieren von Quellcode und verwenden dann den Quellcode für die Anwendungen entwickelt werden.  
  
## Aspekte der grafischen domänenspezifischen Entwicklung  
 Eine grafische domänenspezifische Sprache muss die folgenden Funktionen enthalten:  
  
-   Notation  
  
-   Domänenmodell  
  
-   Generierung Artefakt  
  
-   Serialisierung  
  
-   Integration in Visual Studio  
  
### Notation  
 Eine domänenspezifische Sprache muss einen verhältnismäßig kleinen Satz von Elementen verfügen, die auf einfache Weise definiert werden und erweitert werden können, um domänenspezifische Konstrukte darzustellen.  Eine Notation umfasst Formen, die die Elemente darstellen und Konnektoren, die die Beziehungen zwischen Elementen darstellen, in einer grafischen Diagrammoberfläche.  In [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]können die Formen erweitert werden und verfeinert werden, um die Elemente der domänenspezifischen Sprache darstellt.  
  
### Domänen\-Modell  
 Eine domänenspezifische Sprache muss die Menge von Elementen und Beziehungen zwischen ihnen in eine zusammenhängende Grammatik kombinieren.  Sie muss außerdem definieren, ob Kombinationen von Elementen und Beziehungen gültig sind.  Zum Beispiel verhindern zirkuläre in der Regel Programmiersprachen Vererbung, das in der Klasse ist eine weitere Klasse abgeleitet und die zweite Klasse wird von der ersten Klasse abgeleitet.  Einschränkungen können auch verwendet werden, um Geschäftslogik auszudrücken, z. B. eine Person kann kein abhängiges Element sein.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Einschränkungen verwendet, um die Arten von Einschränkungen auszudrücken, die die meisten domänenspezifischen Sprache benötigen.  
  
### Artefakt\-Generierung  
 Einer der wichtigsten Zwecke einer domänenspezifischen Sprache ist ein Artefakt, z. B. Quellcode, einer XML\-Datei oder mehrere andere verwendbare Daten zu generieren.  In der Regel bedeutet eine Änderung im Modell eine Änderung des Artefakts.  Sie können [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] verwenden, um Artefakte zu generieren und erneut zu generieren, wenn Sie das Modell ändern.  
  
### Serialisierung  
 Eine domänenspezifische Sprache muss in einigen Form beibehalten werden, die bearbeitet werden, gespeichert sind, werden geschlossen und erneut geladen werden kann.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] verwendet ein XML\-Format, das Sie definieren und anpassen können, wie die domänenspezifische Sprache serialisiert oder beibehalten wird.  
  
### Integration in Visual Studio  
 Da [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gehostet wird, erweitert es viele [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Fenster und Steuerelemente.  Sie können auch das Verhalten von Menübefehlen, von Toolboxelementen und anderen Elementen der Benutzeroberfläche anpassen.  
  
 Sie können ein Modell Bus\-Adapter für die domänenspezifische Sprache erstellen.  Dieser Adapter können Sie ein Modell und Elemente innerhalb eines Modells verweisen und können Sie Code schreiben, der eine Instanz des DSL zugreifen und aktualisieren kann.  Mit dem Bus Modell leistungsfähigen Mechanismus zur verwenden, können Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungen schreiben, die mit mehreren Modellen arbeiten.  Sie können auch eigenständige Anwendungen schreiben, die mit Modellen arbeiten.  Weitere Informationen finden Sie unter [Integrieren von Modellen mit Visual Studio\-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## Vorteile von domänenspezifischen Entwicklung  
 Eine domänenspezifische Sprache kann die folgenden Vorteile bieten:  
  
-   Enthält Konstrukte, die genau das Problem der passen.  
  
     Anders als allgemeine Sprachen besteht eine domänenspezifische Sprache Elementen und Beziehungen, die direkt die Logik des Problems leerzeichens darstellen.  Beispielsweise muss eine Versicherungspolice\-Anwendung Richtlinien für Elemente und Eine enthalten.  Eine domänenspezifische Sprache erleichtert die Anwendung zu entwickeln und sucht der Fehler behoben und Logik.  
  
-   Lässt Nicht Entwickler und Personen, die die Domäne nicht kennen, den Gesamtaufbau verstehen.  
  
     Wenn Sie eine grafische domänenspezifische Sprache verwenden, können Sie eine grafische Darstellung der Domäne erstellen, damit Entwickler nicht den Entwurf der Anwendung leichter verstehen können.  
  
-   Ermöglicht es einfacher, einen Prototyp der endgültigen Anwendung zu erstellen.  
  
     Entwickler können den Code verwenden ihr Modell generiert, um eine Prototyp\-Anwendung zu erstellen, die sie anzeigen können den Client.  
  
## Der Prozess der Entwicklung domänenspezifischen  
 Die meisten Software\-Entwicklerteams, die domänenspezifische Sprachen verwenden, führen die folgenden Schritte aus, um die Modelle zu erstellen und zu verwenden:  
  
-   Das Team unterscheidet die variablen Teile der Domäne aus den Teilen, die niemals ändern.  
  
-   Die Entwickler schreiben Code für das Basisstationen und Urlaub Namespaceerweiterung zeigt für variable Teile.  
  
-   Der Führungs softwareentwickler oder der Architekt erstellt eine domänenspezifische Sprache, die die Entwurfsmuster der Basisstationen der Domäne enthält und die Erweiterung für die variablen Teile zeigt.  
  
-   Der Führungs softwareentwickler oder der Architekt stellt die domänenspezifische Sprache für Entwickler der verschiedenen Anwendungen bereit, die vom Team erstellt.  
  
-   Jeder Entwickler erstellt ein Modell, das sich auf die jeweilige Anwendung gilt.