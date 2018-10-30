---
title: Übersicht über domänenspezifische Sprachtools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c01116ee4a4b0edc43a6277db7725e8d962bd607
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49839322"
---
# <a name="overview-of-domain-specific-language-tools"></a>Übersicht über domänenspezifische Sprachtools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domain-Specific-Sprachtools (DSL-Tools), die in gehostet werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], können Sie eine domänenspezifische Sprache zu entwerfen, und generieren Sie dann alle Elemente, die Benutzer benötigen, um Modelle zu erstellen, die von der Sprache basieren.  
  
 Die folgenden Tools sind in DSL-Tools enthalten:  
  
-   Ein Projektassistent, die unterschiedliche Vorlagen verwendet werden, können Sie mit der Entwicklung Ihrer domänenspezifischen Sprache beginnen.  
  
-   Einem grafischen Designer zum Erstellen und Bearbeiten der Definition einer domänenspezifischen Sprache.  
  
-   Eine Überprüfung-Engine, die sicherstellt, dass die Definition einer domänenspezifischen Sprache wohlgeformt ist, und Fehler und Warnungen angezeigt, wenn Probleme auftreten.  
  
-   Ein Code-Generator, der eine domänenspezifischen Sprachdefinition als Eingabe akzeptiert und Quellcode als Ausgabe erzeugt.  
  
## <a name="the-dsl-tools-solution"></a>Der DSL-Tools-Projektmappe  
 Der Domain-Specific-Designer-Assistent bietet die folgenden Vorlagen:  
  
- Aufgabenverlauf  
  
- Klassendiagramme  
  
- Minimale Sprache  
  
- Komponentenmodelle  
  
- Minimaler WPF  
  
- Minimale Windows.Forms  
  
- DSL-Bibliothek  
  
  Weitere Informationen finden Sie unter [Auswählen einer Lösungsvorlage für Domain-Specific Language](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
  Der Assistent erstellt eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projektmappe mit den folgenden Projekten:  
  
- DSL  
  
   Dsl-Projekt definiert, die einer domänenspezifischen Sprache und der zugehörigen Tools bearbeiten und verarbeiten.  
  
- **DslPackage**  
  
   DslPackage-Projekt bestimmt, wie die Language-Tools integrieren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>Der Grafischen Benutzeroberfläche des DSL-Tools  
 Sie können die grafische Benutzeroberfläche des DSL-Tools verwenden, so Ihre DSL-Elementen und Beziehungen hinzu. Nachdem Sie die Elemente hinzugefügt haben, können Sie ihre Darstellung definieren, indem Sie an, die Formen, Anpassen von Farben und Decorator-Elemente hinzufügen. Sie können auch die Elemente zur Toolbox hinzufügen.  
  
## <a name="validation-in-dsl-tools"></a>Validierung in DSL-Tools  
 DSL bietet es sich um eine Ebene der Überprüfung, um sicherzustellen, dass das Domänenmodell die Mindestanforderungen für die codegenerierung erfüllt. Wenn Sie Ihre eigenen domänenspezifischen Sprache erstellen, würden Sie in der Regel eigene Überprüfung, um Ihre Geschäftsregeln für die Logik auszudrücken hinzufügen. Weitere Informationen zu benutzerdefinierten Validierung, finden Sie unter [Validierung in einer domänenspezifischen Sprache](../modeling/validation-in-a-domain-specific-language.md).  
  
 Es wird empfohlen, dass Ihre Domain-Specific Languge häufig, beim Entwerfen überprüfen. Wenn Ihre Domain-Specific Languge Validierungsfehler aufweist, nicht Quellcode generiert werden. Der Prozess zum Generieren von Quellcode aus den Vorlagen wird durchgeführt, indem Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des Projektmappen-Explorer. Wenn Sie die Definition der Sprache ändern, stellen Sie außerdem sicher, **alle Vorlagen transformieren**. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer domänenspezifischen Sprachlösung](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Anpassung der DSL-Tools  
 Sie können zusätzlichen Code, um das Verhalten des Modells zu verfeinern und zum Definieren der Einschränkungen für die Sprache angeben. Falls erforderlich, können Sie erhebliche Änderungen vornehmen, indem Sie die Textvorlagen ändern.  
  
## <a name="distributing-your-dsl-solution"></a>Verteilen Ihrer DSL-Projektmappe  
 DSL-Tools generiert ein Paket, das in gehosteten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Das Paket zeigt eine Toolbox, einem DSL-Explorer und anderen UI-Elementen, die Benutzern das Erstellen von Modellen mit einer domänenspezifischen Sprache zu ermöglichen.  
  
 Wenn Sie und führen Sie die DSL-Tools-Lösung [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], eine zweite Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] erfahren Sie, wie die domänenspezifischen Sprache für den Benutzer der Sprache aussieht. Nachdem Sie überprüft haben, dass alles ordnungsgemäß funktioniert, können Sie verteilen die `.vsix` Datei, die Sie im Ordner "Build" der DslPackage-Projekt finden werden. Diese Datei kann verwendet werden, um die DSL als eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterung auf anderen Computern.  Weitere Informationen finden Sie unter [Bereitstellen von domänenspezifischen Sprachlösungen](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Die experimentelle Instanz](../extensibility/the-experimental-instance.md)   
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



