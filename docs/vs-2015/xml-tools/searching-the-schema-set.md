---
title: Durchsuchen des Schemasets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6ce05cbaf203649ce62d13285f7304c04be6497
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512681"
---
# <a name="searching-the-schema-set"></a>Durchsuchen des Schemasets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Durchsuchen des Schemasets](https://docs.microsoft.com/visualstudio/xml-tools/searching-the-schema-set).  
  
  
Im XML-Schema-Explorer stehen Ihnen die folgenden Methoden zum Durchsuchen des Schemasets zur Verfügung:  
  
-   Schlüsselwortsuche  
  
-   Schemaspezifische Suche  
  
## <a name="keyword-search"></a>Schlüsselwortsuche  
 Durchführen von Schlüsselwortsuchen durch Eingabe einer Teilzeichenfolge in der **Schlüsselwortsuche** Textfeld der XML-Schema-Explorer-Symbolleiste.  
  
 ![XML-Schema-Explorer-Schlüsselwortsuche](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 Der XML-Schema-Explorer durchsucht das Schemaset nach Folgendem:  
  
-   Alle `name`- oder `ref`-Attribute, die mit dem angegebenen Schlüsselwort übereinstimmen. So können Sie anhand des Namens nach Elementen, Attributen, Typen usw. suchen.  
  
-   Die `schemaLocation`-Attribute von Include-Anweisungen.  
  
-   Die `namespace`-Attribute von Import-Anweisungen.  
  
## <a name="schema-specific-search"></a>Schemaspezifische Suche  
 Der XML-Schema-Explorer enthält auch integrierte Suchfunktionen, auf die Sie über das Kontextmenü des XML-Schema-Explorers zugreifen. Weitere Informationen zu verfügbaren Kontextmenüs finden Sie unter [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md). Sie können auch eine schemaspezifische Suche aus der Ausgangsansicht ausführen; Weitere Informationen finden Sie im Abschnitt "Details zum Schemaset" in der [Ausgangsansicht](../xml-tools/start-view.md) Thema.  
  
## <a name="displaying-and-navigating-search-results"></a>Anzeigen von Suchergebnissen und Navigieren in den Ergebnissen  
 Nach der Suche wird der Symbolleiste ein Bereich mit der Ergebniszusammenfassung der Suche hinzugefügt. Die Suchergebnisse werden auch im XML-Schema-Explorer hervorgehoben und auf der vertikalen Bildlaufleiste durch Teilstriche markiert. Sie können die Suchergebnissen navigieren, indem die **wechseln Sie zum nächsten Suchergebnis** und **wechseln Sie zum vorherigen Suchergebnis** Schaltflächen auf den Bereich der XML-Schema-Explorer-Symbolleiste, drücken Sie die Tasten mit F3 und UMSCHALT + F3; oder durch Klicken auf die Teilstriche in der Bildlaufleiste.  
  
 Sie können die Ergebnisse der Suche mit dem Arbeitsbereich hinzufügen, indem Sie auf die **hervorgehobene Knoten zu Arbeitsbereich hinzufügen** auf den Bereich auf die Schaltfläche.  
  
 ![XML-Schema-Explorer-Suchergebnis](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Löschen der Suchergebnisse  
 Um die Suchergebnisse zu löschen, klicken Sie auf die **x** im Bereich Zusammenfassung der Ergebnisse der Suche für XML-Schema-Explorer-Symbolleiste die Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)



