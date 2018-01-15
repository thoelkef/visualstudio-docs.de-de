---
title: "Übersicht über domänenspezifische Sprachtools | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7c1a163e50e2f237430ba13d57a76cfc0d6b1d67
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="overview-of-domain-specific-language-tools"></a>Übersicht über domänenspezifische Sprachtools
Domänenspezifische Sprachtools (DSL Tools), die in gehostet werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ermöglichen eine domänenspezifische Sprache zu entwerfen und generieren Sie alle Elemente, die Benutzer benötigen, um Modelle zu erstellen, die auf der Sprache basieren.  
  
 DSL-Tools gehören die folgenden Tools:  
  
-   Ein Projektassistent, die Projektmappenvorlagen für andere verwendet wird, können Sie mit der Entwicklung einer domänenspezifischen Sprache beginnen.  
  
-   Einem grafischen Designer zum Erstellen und bearbeiten die Definition einer domänenspezifischen Sprache.  
  
-   Ein Validierungsmodul, die sicherstellt, dass die Definition einer domänenspezifischen Sprache wohlgeformt ist und Fehler und Warnungen angezeigt, wenn Probleme vorliegen.  
  
-   Ein Code-Generator, der eine Definition einer domänenspezifischen Sprache als Eingabe akzeptiert und Quellcode als Ausgabe erzeugt.  
  
## <a name="the-dsl-tools-solution"></a>DSL-Tools-Lösung  
 Der Domain-Specific-Designer-Assistent stellt die folgenden Lösungsvorlagen bereit:  
  
-   Aufgabenverlauf  
  
-   Klassendiagramme  
  
-   Minimale Sprache  
  
-   Komponentenmodelle  
  
-   Minimale WPF  
  
-   Minimale Windows.Forms  
  
-   DSL-Bibliothek  
  
 Weitere Informationen finden Sie unter [Auswählen einer domänenspezifischen Sprache Projektmappenvorlage](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 Der Assistent erstellt eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung mit den folgenden Projekten:  
  
-   DSL  
  
     Dsl-Projekt definiert die domänenspezifische Sprache und die zugehörigen Tools bearbeiten und verarbeiten.  
  
-   **DslPackage**  
  
     Das Projekt DslPackage bestimmt, wie die Sprachtools integriert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>Die Grafische Benutzeroberfläche des DSL-Tools  
 Sie können die grafische Benutzeroberfläche DSL-Tools verwenden, Hinzufügen von Elementen und Beziehungen zu einer domänenspezifischen Sprache. Nachdem Sie die Elemente hinzugefügt haben, können Sie ihre Darstellung Formen zuordnen und Anpassen von Farben hinzufügen von Decorator-Elementen definieren. Sie können auch die Elemente zur Toolbox hinzufügen.  
  
## <a name="validation-in-dsl-tools"></a>Die Validierung in DSL-Tools  
 DSL bietet eine Überprüfung, um sicherzustellen, dass das Domain-Modell für die codegenerierung die Mindestanforderungen erfüllt. Wenn Sie eigene domänenspezifische Sprache erstellen, würden Sie in der Regel Ihre eigene Überprüfung aus, um Ihre Logik Geschäftsregeln express hinzufügen. Weitere Informationen zur benutzerdefinierten Validierung finden Sie unter [Überprüfung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
 Es wird empfohlen, dass Ihre einer domänenspezifischen Sprache häufig überprüfen, wenn Sie es entwerfen. Wenn Ihre einer domänenspezifischen Sprache Validierungsfehler vorhanden sind, können keine Quellcode generiert werden. Der Vorgang zum Generieren von Quellcode aus den Vorlagen wird ausgeführt, indem Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer. Wenn Sie die Sprachendefinition ändern, stellen Sie außerdem sicher, dass **alle Vorlagen transformieren**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer domänenspezifischen Sprache Lösung](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Anpassung der DSL-Tools  
 Sie können zusätzlichen Code, um das Verhalten des Modells zu verfeinern und zum Definieren der Einschränkungen für Ihre Sprache bereitstellen. Bei Bedarf können Sie erhebliche Änderungen vornehmen, indem Sie die Textvorlagen ändern.  
  
## <a name="distributing-your-dsl-solution"></a>Verteilen der DSL-Projektmappe  
 DSL-Tools generiert ein Paket, das in gehosteten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Das Paket zeigt eine Toolbox, einen DSL-Explorer und andere Elemente der Benutzeroberfläche, mit die Benutzer, die Modelle mit einer domänenspezifischen Sprache erstellen können.  
  
 Beim Erstellen und Ausführen die Projektmappe DSL-Tools in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], eine zweite Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wird gezeigt, wie Ihre einer domänenspezifischen Sprache für den Benutzer der Sprache aussieht. Nachdem Sie überprüft haben, dass alles ordnungsgemäß funktioniert, können Sie verteilen die `.vsix` -Datei, die Sie im Ordner "Builds" des Projekts DslPackage erwarten können. Diese Datei kann zum Installieren der DSL als eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung auf anderen Computern.  Weitere Informationen finden Sie unter [Bereitstellen einer domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)   
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)