---
title: Überprüfen des Systems während der Entwicklung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 03cac924853f4348faabd773260a9512c2d82b6b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760975"
---
# <a name="validate-your-system-during-development"></a>Überprüfen des Systems während der Entwicklung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio unterstützt Sie dabei, die Software mit den Anforderungen der Benutzer und der Architektur des Systems in Einklang zu bringen.  
  
 Informationen dazu, welche Versionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Hauptaufgaben  
 Überprüfen Sie die Software mithilfe der folgenden Aufgaben.  
  
|**Aufgaben**|**Verwandte Themen**|  
|---------------|---------------------------|  
|**Stellen Sie sicher, dass das Modell konsistent ist:**<br /><br /> Abhängig davon, wie Modelle im Projekt verwendet und interpretiert werden, kann es sinnvoll sein, einige Kombinationen von Elementen nicht zuzulassen. Sie können z.B. durch eine Einschränkung festlegen, dass UML-Klassen immer [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-kompatible Namen haben müssen. Solche Einschränkungen können in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterungen definiert werden.|-   [Überprüfen des UML-Modells](../modeling/validate-your-uml-model.md)<br />-   [Definieren von validierungseinschränkungen für UML-Modelle](../modeling/define-validation-constraints-for-uml-models.md)|  
|**Stellen Sie sicher, dass die Software die Anforderungen der Benutzer erfüllt**:<br /><br /> Sie können Anforderungen und architektonische Modelle verwenden, um die Tests des Systems und seiner Komponenten zu organisieren. Durch diese Vorgehensweise können Sie sicherstellen, dass die Anforderungen, die für die Benutzer und andere Projektbeteiligte wichtig sind, getestet werden. Außerdem können Sie dadurch die Tests schneller aktualisieren, wenn sich die Anforderungen ändern.|-   [Entwickeln von Tests aus einem Modell](../modeling/develop-tests-from-a-model.md)|  
|**Stellen Sie sicher, dass die Software mit dem vorgesehenen Entwurf des Systems konsistent bleibt:**<br /><br /> Ebenendiagramme beschreiben die vorgesehenen Abhängigkeiten zwischen den Komponenten der Anwendung. Während der Entwicklung können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Code dem vorgesehenen Entwurf entsprechen.|-   [Erstellen von Ebenendiagrammen aus Ihrem code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Überprüfen von Code mit Ebenendiagrammen](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
|**Kategorie**|**Links**|  
|------------------|---------------|  
|**Videos**|![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug sieben: Verstehen von Code und Systementwurf mit Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Entwerfen einer Anwendung mit einem Ebenendiagramm](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![Link zum Video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN-Reihe: Überprüfen von Code mit Ebenendiagrammen](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|-   [Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technische Artikel und Journale**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Siehe auch  
 [Testen der Anwendung](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)   
 [Erweitern von UML-Modellen und-Diagrammen](../modeling/extend-uml-models-and-diagrams.md)   
 [Modellieren von benutzeranforderungen](../modeling/model-user-requirements.md)   
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)



