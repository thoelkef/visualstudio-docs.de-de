---
title: "Überprüfen Sie das System während der Entwicklung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams
ms.assetid: c9dafb47-7b1d-4c72-9432-d43be3db1799
caps.latest.revision: 37
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: d35e357a62c467d20f5a97a469ac5f89324b4391
ms.lasthandoff: 02/22/2017

---
# <a name="validate-your-system-during-development"></a>Überprüfen des Systems während der Entwicklung
Visual Studio unterstützt Sie dabei, die Software mit den Anforderungen der Benutzer und der Architektur des Systems in Einklang zu bringen.  
  
 Welche Versionen von Visual Studio die einzelnen Features unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="key-tasks"></a>Hauptaufgaben  
 Überprüfen Sie die Software mithilfe der folgenden Aufgaben.  
  
|**Tasks** (MSBuild-Aufgaben)|**Verwandte Themen**|  
|---------------|---------------------------|  
|**Stellen Sie sicher, dass die Software die Anforderungen der Benutzer erfüllt**:<br /><br /> Sie können Anforderungen und architektonische Modelle verwenden, um die Tests des Systems und seiner Komponenten zu organisieren. Durch diese Vorgehensweise können Sie sicherstellen, dass die Anforderungen, die für die Benutzer und andere Projektbeteiligte wichtig sind, getestet werden. Außerdem können Sie dadurch die Tests schneller aktualisieren, wenn sich die Anforderungen ändern.|-   [Entwickeln von Tests aus einem Modell](../modeling/develop-tests-from-a-model.md)|  
|**Stellen Sie sicher, dass Ihre Software mit dem vorgesehenen Entwurf des Systems konsistent bleibt:**<br /><br /> Abhängigkeitsdiagramme beschreiben die beabsichtigten Abhängigkeiten zwischen den Komponenten der Anwendung. Während der Entwicklung können Sie überprüfen, ob die tatsächlichen Abhängigkeiten im Code dem vorgesehenen Entwurf entsprechen.|-   [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md)|  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
|**Kategorie**|**Links**|  
|------------------|---------------|  
|**Videos**|![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Doug sieben: Verstehen von Code und Systementwurf mit Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkId=216100)<br /><br /> ![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") [Channel 9: Entwerfen einer Anwendung mit einem Abhängigkeitsdiagramm](http://go.microsoft.com/fwlink/?LinkID=201117)<br /><br /> ![Link zu Video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN-Reihe: Vorgehensweise beim Überprüfen von Code mit Abhängigkeitsdiagramme](http://go.microsoft.com/fwlink/?LinkID=214405)|  
|**Foren**|-   [Visual Studio-Visualisierungs & Modellierungstools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Visual Studio-Visualisierungs & Modeling SDK (DSL-Tools)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogs**|-   [Visual Studio ALM + Team Foundation Server-Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Technische Artikel und Journale**|[MSDN Architecture Center](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Siehe auch  
 [Testen der Anwendung](https://www.visualstudio.com/en-gb/docs/test/overview)   
 [Modellanforderungen](../modeling/model-user-requirements.md)   
 [Analysieren und Modellieren der Architektur](../modeling/analyze-and-model-your-architecture.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

