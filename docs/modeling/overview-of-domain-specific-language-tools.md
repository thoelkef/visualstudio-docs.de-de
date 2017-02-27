---
title: "&#220;bersicht &#252;ber dom&#228;nenspezifische Sprachtools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 54
---
# &#220;bersicht &#252;ber dom&#228;nenspezifische Sprachtools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Domänenspezifische Sprachtoole \(DSL\-Toole\), die in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gehostet, eine domänenspezifische Sprache entworfen und anschließend werden alle generieren lassen, dass Benutzer benötigen Modelle erstellen, die auf Grundlage der Sprache sind.  
  
 Die folgenden Tools werden in DSL\-Toolen enthalten:  
  
-   Der Projekt\-Assistent, der verschiedene von Projektmappen verwendet, starten Sie die Entwicklung von domänenspezifischen Sprache.  
  
-   Ein grafischen Designer zum Erstellen und Bearbeiten von domänenspezifischen Sprache. Definition  
  
-   Ein Validierungsmodul, die sicherstellen, dass die domänenspezifische Sprachen wohl geformt ist und zeigt die Definition Fehler und Warnungen an, wenn Probleme auftreten.  
  
-   Ein Codegenerator, der eine domänenspezifische Sprachen als Eingabe verwendet und Quellcode Definition als Ausgabe erzeugt.  
  
## Die DSL\-Tool\-Projektmappe  
 Der domänenspezifische Designer\-Assistent Lösungen bietet die folgenden Vorlagen bereit:  
  
-   Aufgaben\-Fluss  
  
-   Klassendiagramme  
  
-   Minimale Sprache  
  
-   Teilmodelle  
  
-   Minimales WPF  
  
-   Minimales Windows.Forms  
  
-   DSL\-Bibliothek  
  
 Weitere Informationen finden Sie unter [Auswählen einer Lösungsvorlage für eine domänenspezifische Sprache](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 Der Assistent erstellt eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektmappe, die die folgenden Projekte enthält:  
  
-   Dsl  
  
     Das dsl\-Projekt definiert die domänenspezifische Sprache und ihre Bearbeitung und Verarbeitung Tools.  
  
-   **DslPackage**  
  
     Das DslPackage\-Projekt bestimmt, wie die Tools für Sprachen mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]integrieren.  
  
## Die DSL\-Tool\-grafische Schnittstelle  
 Sie können die DSL\-Tool grafische Oberfläche können Sie Elemente und Beziehungen domänenspezifischen Sprache hinzugefügt werden soll.  Nachdem Sie die Elemente hinzugefügt haben, können Sie deren Darstellung definieren, indem Sie diese Formen zuordnen und Farben anpassen Decorator\-Elemente hinzufügen.  Sie können die Elemente der Toolbox hinzufügen.  
  
## Validierung auf DSL\-Toolen  
 Dsl stellt eine Ebene Validierung, um sicherzustellen, dass das Domänenmodell dem Grundbedarf für die Codegenerierung erfüllt.  In der Regel erstellen, wenn Sie besitzen Sie domänenspezifische Sprache, die Sie hinzufügen, wird eine Validierung verfügen, um die Geschäftslogik regeln auszudrücken.  Weitere Informationen über benutzerdefinierte Validierung finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
 Es wird empfohlen, die häufig domänenspezifische Sprache überprüfen, wenn sie entwerfen.  Wenn die domänenspezifische Sprache Validierungsfehler aufweist, können Sie Quellcode konnte nicht generiert werden.  Beim Generieren von Quellcode aus Vorlagen wird ausgeführt, indem auf **Alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen\-Explorers klicken.  Jedes Mal, wenn Sie die Definition der Sprache ändern, vergewissern Sie sich auch auf **Alle Vorlagen transformieren**.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## Anpassung von DSL\-Toolen  
 Sie können zusätzlichen Code bereitstellen, um das Verhalten des Modells zu verfeinern und Einschränkungen bezüglich der Sprache zu definieren.  Bei Bedarf können Sie wesentliche Änderungen vornehmen, indem Sie die Textvorlagen ändern.  
  
## Die DSL\-Projektmappe verteilen  
 DSL\-Toole generiert ein Paket, das in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gehostet wird.  Das Paket wird eine Toolbox ein DSL\-Explorer und andere Benutzeroberflächenelemente an, die von Benutzern Modellen erstellen, indem sie die domänenspezifische Sprache verwenden.  
  
 Wenn Sie die Projektmappe DSL\-Tool in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]erstellen und ausführen, wird eine zweite Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erläutert, wie die domänenspezifische Sprache für den Benutzer sieht der Sprache. Nachdem Sie sicherstellen, dass alles ordnungsgemäß funktioniert, können Sie die `.vsix` Datei verteilen, die Sie im Buildordner des DslPackage\-Projekts suchen.  Diese Datei kann verwendet werden, um das DSL als [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung auf anderen Computern zu installieren.  Weitere Informationen finden Sie unter [Bereitstellen von domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).  
  
## Siehe auch  
 [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)