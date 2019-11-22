---
title: Validate your system during development | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fec3595ba7886f5ba979c35e9441ab108174726
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301346"
---
# <a name="validate-your-system-during-development"></a>Überprüfen des Systems während der Entwicklung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio unterstützt Sie dabei, die Software mit den Anforderungen der Benutzer und der Architektur des Systems in Einklang zu bringen.

 Informationen dazu, welche Versionen von Visual Studio die einzelnen Funktionen unterstützen, finden Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="key-tasks"></a>Hauptaufgaben
 Überprüfen Sie die Software mithilfe der folgenden Aufgaben.

|**Tasks (Aufgaben)**|**Verwandte Themen**|
|---------------|---------------------------|
|**Make sure your model is consistent:**<br /><br /> Abhängig davon, wie Modelle im Projekt verwendet und interpretiert werden, kann es sinnvoll sein, einige Kombinationen von Elementen nicht zuzulassen. Sie können z.B. durch eine Einschränkung festlegen, dass UML-Klassen immer [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]-konforme Namen haben müssen. Solche Einschränkungen können in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Erweiterungen definiert werden.|-   [Validate your UML model](../modeling/validate-your-uml-model.md)<br />-   [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md)|
|**Stellen Sie sicher, dass die Software die Anforderungen der Benutzer erfüllt**:<br /><br /> Sie können Anforderungen und architektonische Modelle verwenden, um die Tests des Systems und seiner Komponenten zu organisieren. Durch diese Vorgehensweise können Sie sicherstellen, dass die Anforderungen, die für die Benutzer und andere Projektbeteiligte wichtig sind, getestet werden. Außerdem können Sie dadurch die Tests schneller aktualisieren, wenn sich die Anforderungen ändern.|-   [Develop tests from a model](../modeling/develop-tests-from-a-model.md)|
|**Stellen Sie sicher, dass die Software mit dem vorgesehenen Entwurf des Systems konsistent bleibt:**<br /><br /> Ebenendiagramme beschreiben die vorgesehenen Abhängigkeiten zwischen den Komponenten der Anwendung. Während der Entwicklung können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Code dem vorgesehenen Entwurf entsprechen.|-   [Create layer diagrams from your code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Validate code with layer diagrams](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="external-resources"></a>Externe Ressourcen

|**Kategorie**|**Links**|
|------------------|---------------|
|**Videos**|![link to video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug Seven: Code Understanding and System Design with Visual Studio 2010](https://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![link to video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Architecting an Application using a Layer Diagram](https://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![link to video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN How Do I Series: How to Validate Code using Layer Diagrams](https://go.microsoft.com/fwlink/?LinkID=214405)|
|**Foren**|-   [Visual Studio-Visualisierungs- & Modellierungstools](https://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio Visualization & Modeling SDK (DSL Tools)](https://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogs**|-   [Visual Studio ALM + Team Foundation Server Blog](https://go.microsoft.com/fwlink/?LinkID=201340)|
|**Technische Artikel und Journale**|[MSDN Architecture Center](https://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Siehe auch
 [Testing the application](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Model user requirements](../modeling/model-user-requirements.md) [Analyzing and Modeling Architecture](../modeling/analyze-and-model-your-architecture.md)
