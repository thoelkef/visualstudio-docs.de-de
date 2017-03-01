---
title: "Strukturieren Sie Ihre Lösung für die Modellierung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 14
author: alexhomer1
ms.author: ahomer
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
ms.openlocfilehash: b817affe78e53e0d010f5bb62676192fa90fd49e
ms.lasthandoff: 02/22/2017

---
# <a name="structure-your-modeling-solution"></a>Strukturieren der Modellierungslösung
Um Modelle in einem Entwicklungsprojekt effizient zu verwenden, müssen die Teammitglieder gleichzeitig an Modellen aus verschiedenen Teilen des Projekts arbeiten können. In diesem Thema wird ein Schema zum Aufteilen der Anwendung in verschiedene Teile vorgeschlagen, die den Ebenen in einem allgemeinen Ebenendiagramm entsprechen.  
  
 Um schnell mit einem Projekt oder Unterprojekt beginnen zu können, ist es hilfreich, über eine Projektvorlage zu verfügen,die der gewählten Projektstruktur folgt. In diesem Thema wird beschrieben, wie eine solche Vorlage erstellt und verwendet wird.  
  
 In diesem Thema wird davon ausgegangen, dass Sie an einem Projekt arbeiten, das so groß ist, dass mehrere Teammitglieder erforderlich sind, und an dem möglicherweise mehrere Teams beteiligt sind. Der Code und die Modelle des Projekts sind in einem Quellcodeverwaltungssystem wie z. B. [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] gespeichert. Zumindest einige Teammitglieder verwenden Visual Studio zum Entwickeln von Modellen, und andere Teammitglieder können die Modelle mit anderen Versionen von Visual Studio anzeigen.  
  
 Welche Versionen von Visual Studio jedes Tool und Modellierungsfunktionen unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Projektmappenstruktur  
 In einem mittleren oder großen Projekt basiert die Struktur des Teams auf der Struktur der Anwendung. Jedes Team verwendet eine Visual Studio-Projektmappe.  
  
#### <a name="to-divide-an-application-into-layers"></a>So unterteilen Sie eine Anwendung in Ebenen  
  
1.  Lassen Sie die Struktur Ihrer Projektmappen auf der Struktur der Anwendung basieren, etwa einer Webanwendung, Dienstanwendung oder Desktopanwendung. Behandelt verschiedene allgemeine Architekturen [Anwendungsarchetypen in der Microsoft Application Architecture Guide](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2.  Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektmappe, die wir als Architektur-Projektmappe bezeichnen. Diese Projektmappe wird zur Erstellung des allgemeinen Entwurfs des Systems verwendet. Es enthält Modelle, jedoch keinen Code.  
  
     Fügen Sie ein Abhängigkeitsdiagramm zu dieser Lösung. Die Abhängigkeitsdiagramm zeichnen Sie die Architektur, die Sie für Ihre Anwendung ausgewählt haben. Das Diagramm kann beispielsweise die folgenden Ebenen und die Abhängigkeiten zwischen ihnen zeigen: Präsentation, Geschäftslogik und Daten.  
  
4.  Erstellen Sie eine separate Visual Studio-Lösung für jede Ebene im Architekturdiagramm Abhängigkeit.  
  
     Diese Projektmappen werden verwendet, um den Code für die Ebenen zu entwickeln.  
  
5.  Erstellen Sie Modelle, die die Entwürfe der Ebenen und die Konzepte, die auf alle Ebenen darstellt. Ordnen Sie die Modelle so an, dass alle Modelle in der Architektur-Projektmappe und die relevanten Modelle in den einzelnen Ebenen angezeigt werden können.  
  
     Sie können dies mit einem der folgenden Verfahren erreichen. Bei der ersten Alternative wird für jede Ebene ein separates Modellierungsprojekt erstellt, und bei der zweiten wird ein einzelnes Modellierungsprojekt erstellt, das von den Ebenen gemeinsam genutzt wird.  
  
    ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>So verwenden Sie ein separates Modellierungsprojekt für jede Ebene  
  
    1.  Erstellen Sie in jeder Ebenenprojektmappe ein Modellierungsprojekt.  
  
         Dieses Modell enthält Diagramme, in denen die Anforderungen und Entwurf der jeweiligen Ebene beschrieben. Sie können auch Abhängigkeitsdiagramme enthalten, die geschachtelte Ebenen anzeigen.  
  
         Sie verfügen jetzt über ein Modell für jede Ebene sowie über ein Modell für die Anwendungsarchitektur. Jedes Modell ist in einer eigenen Projektmappe enthalten. Dies ermöglicht es Teammitgliedern, gleichzeitig an den Ebenen zu arbeiten.  
  
    2.  Fügen Sie der Architektur-Projektmappe das Modellierungsprojekt jeder Ebenenprojektmappe hinzu. Öffnen Sie hierzu die Architektur-Projektmappe. Im Projektmappen-Explorer mit der Maustaste des Knotens Projektmappe, zeigen Sie auf Hinzufügen, und klicken Sie dann auf **vorhandenes Projekt**. Navigieren Sie zum Modellierungsprojekt (.modelproj) in einer Ebenenprojektmappe.  
  
         Jedes Modell wird jetzt in zwei Projektmappen angezeigt: der Start-Projektmappe und der Architektur-Projektmappe.  
  
    3.  Fügen Sie dem Modellierungsprojekt jeder Ebene ein Abhängigkeitsdiagramm hinzu. Beginnen Sie mit einer Kopie der Abhängigkeit Architekturdiagramm. Sie können Teile löschen, die keine Abhängigkeiten des Diagramms abhängig sind.  
  
         Sie können auch Abhängigkeitsdiagramme hinzufügen, die die ausführliche Struktur dieser Ebene darstellen.  
  
         Diese Diagramme werden verwendet, um den Code zu überprüfen, der in dieser Ebene entwickelt wird.  
  
    4.  Bearbeiten Sie in der Architektur-Projektmappe die Anforderungen und die Entwurfsmodelle für alle Ebenen mit Visual Studio.  
  
         Entwickeln Sie in jeder Ebenenprojektmappe den Code für diese Ebene, der auf das Modell verweist. Wenn Sie die Entwicklung durchführen möchten, ohne den gleichen Computer zum Aktualisieren des Modells zu verwenden, können Sie das Modell lesen und Code entwickeln, indem Sie Versionen von Visual Studio verwenden, die keine Modelle erstellen können. Sie können Code auch aus dem Modell in diesen Versionen generieren.  
  
     Diese Methode stellt sicher, dass keine Störungen von Entwicklern verursacht werden, die die Ebenenmodelle zur gleichen Zeit bearbeiten.  
  
     Da die Modelle getrennt sind, ist es jedoch schwierig, auf allgemeine Konzepte zu verweisen. Jedes Modell muss eine eigene Kopie der Elemente aufweisen, von denen es über andere Ebenen und die Architektur abhängig ist. Das Abhängigkeitsdiagramm in jeder Ebene muss mit der Abhängigkeit Architekturdiagramm synchron gehalten werden. Es ist schwierig, die Synchronisierung beizubehalten, wenn sich diese Elemente ändern, obwohl Sie zu diesem Zweck Tools entwickeln könnten.  
  
    ###### <a name="to-use-a-separate-package-for-each-layer"></a>So verwenden Sie ein separates Paket für jede Ebene  
  
    1.  Fügen Sie in der Projektmappe für jede Ebene das Architektur-Modellierungsprojekt hinzu. Im Projektmappen-Explorer mit der Maustaste des Knotens Projektmappe, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **vorhandenes Projekt**. Das einzelne Modellierungsprojekt kann nun aus allen Projektmappen aufgerufen werden: das Projekt für die Architektur und das Entwicklungsprojekt für jede Ebene.  
  
    2.  Erstellen Sie im freigegebenen Modell, ein Paket für jede Ebene: Wählen Sie im Projektmappen-Explorer das Modellierungsprojekt. Klicken Sie im UML-Modell-Explorer auf die Modell-Stammknoten, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf **Paket**.  
  
         Jedes Paket enthält Diagramme, in denen die Anforderungen und Entwurf der jeweiligen Ebene beschrieben.  
  
    3.  Fügen Sie gegebenenfalls lokale Abhängigkeitsdiagramme für die interne Struktur der einzelnen Ebenen hinzu.  
  
     Diese Methode ermöglicht es, dass die Entwurfselemente der einzelnen Ebenen direkt auf die der Ebenen und gemeinsame Architektur verweisen, von denen sie abhängen.  
  
     Obwohl das gleichzeitige Arbeiten an verschiedenen Paketen Konflikte verursachen kann, sind sie relativ einfach zu lösen, da die Pakete in separaten Dateien gespeichert werden.
  
## <a name="creating-architecture-templates"></a>Erstellen von Architekturvorlagen  
 In der Praxis erstellen Sie nicht alle Visual Studio-Projektmappen zur gleichen Zeit, sondern fügen sie im Laufe des Projekts hinzu. Wahrscheinlich werden Sie auch die dieselbe Projektmappenstruktur für zukünftige Projekte verwenden.  Um schnell neue Projektmappen erstellen zu können, können Sie eine Projektmappen- oder Projektvorlage erstellen. Sie können die Vorlage in einer Visual Studio Integration Extension (VSIX) erfassen, damit Sie sie einfach verteilen und auf anderen Computern installieren können.  
  
 Wenn Sie beispielsweise häufig Projektmappen mit Präsentations-, Geschäfts- und Datenebenen verwenden, können Sie eine Vorlage konfigurieren, die neue Projektmappen mit dieser Struktur erstellt.  
  
#### <a name="to-create-a-solution-template"></a>So erstellen Sie ein Projektmappenvorlage  
  
1.  [Herunterladen und installieren Sie den Assistenten zum Exportieren von Vorlagen](http://go.microsoft.com/fwlink/?LinkId=196686), sofern Sie nicht bereits geschehen.  
  
2.  Erstellen Sie die Projektmappenstruktur, die Sie als Ausgangspunkt für zukünftige Projekte verwenden möchten.  
  
3.  Klicken Sie im Menü **Datei** auf **Vorlage als VSIX exportieren**. Die **Vorlage exportieren als VSIX-Assistenten** wird geöffnet.  
  
4.  Folgen Sie den Anweisungen im Assistenten und wählen Sie die Projekte aus, die in die Vorlage aufgenommen werden sollen, geben Sie einen Namen und eine Beschreibung für die Vorlage an, und geben Sie einen Ausgabespeicherort an.  
  
> [!NOTE]
>  Das Material in diesem Thema wurde aus der Visual Studio Architecture Tooling Guidance+++ abstrahiert und verallgemeinert, die von den Visual Studio ALM Rangers+++ verfasst wurde und aus der Zusammenarbeit zwischen Most Valued Professionals (MVPs), Microsoft-Diensten und Visual Studio-Produktteam und -Autoren entstanden ist [Klicken Sie hier, um das vollständige Anleitungspaket herunterzuladen.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Verwandte Materialien  
 [Organisieren und Verwalten von Modellen](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - video von Clint Edmondson.  
  
 [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md) – Weitere Anleitungen zum Verwalten von Modellen in einem Team  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Verwenden von Modellen im Entwicklungsprozess](../modeling/use-models-in-your-development-process.md)

