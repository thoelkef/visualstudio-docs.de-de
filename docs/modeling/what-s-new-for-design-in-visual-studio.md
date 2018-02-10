---
title: Was &#39; s Entwurf in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c3fe70c36daf9d137e77acf75b9bd712ecf556c7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="what39s-new-for-design-in-visual-studio"></a>Was &#39; s Entwurf in Visual Studio

## <a name="live-dependency-validation"></a>Live abhängigkeitsüberprüfung

Entfernen unerwünschte Abhängigkeiten ist ein wichtiger Teil Ihrer technische Schulden zu verwalten.
Live-Überprüfung der Abhängigkeiten ist jetzt enthalten, genaue Informationen über Probleme und profitiert vollständig, die die neuen Funktionen in der Fehlerliste und -Editor.

![Live abhängigkeitsüberprüfung in Aktion](media/dep-validation-whatsnew-01.png)

Die Möglichkeiten für die Erstellung wurde geändert, um abhängigkeitsüberprüfung vornehmen, bleibt Ihnen erspart und mehr zugegriffen werden kann, ändern die Terminologie von "Ebenendiagramm" in "Abhängigkeit Diagramm".

Die **Architektur** Menü enthält nun einen Befehl, um eine Abhängigkeit Diagramm direkt zu erstellen:

![Live-Abhängigkeit Element im Architektur-Menü](media/dep-validation-whatsnew-02.png)

... und die Eigenschaftsnamen einer Ebene in einem Diagramm Abhängigkeit und ihren Beschreibungen, um aussagekräftigere geändert wurden:

![Live-Abhängigkeit aktualisiert Eigenschaftennamen](media/dep-validation-whatsnew-03.png)

Sie sehen nun die Auswirkungen der Änderungen sofort in die Ergebnisse der Analyse für den aktuellen Code in der Projektmappe jedes Mal, wenn Sie das Diagramm speichern. Sie müssen nicht mehr warten auf den Abschluss des Befehls "Abhängigkeiten überprüfen".

Weitere Informationen finden Sie unter [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/). 
 
## <a name="uml-designers-have-been-removed"></a>UML-Designer wurden entfernt

Die UML-Designer wurden aus dieser Version von Visual Studio Enterprise entfernt.

* UML-Diagramme werden jetzt als XML-Dateien dargestellt.
* UML-Modell-Explorer ist nicht mehr vorhanden.
* Modellierungsobjekt Verweise sind abhängigkeitsüberprüfung nicht mehr verwendet
* Der Knoten "Ebenenverweise" im Projektmappen-Explorer wird nicht mehr angezeigt.
* Die "Überprüfen" Build-Aktion in einem Diagramm Abhängigkeit (Layer) wird nicht mehr verwendet: die Buildaufgabe wurde entfernt 
* Die Projektstruktur wird für Roundtrips zwischen den Versionen beibehalten.
* Sie können weiterhin öffnen, erstellen, bearbeiten, und speichern Sie eine Abhängigkeit (Layer)-Diagramm als XML
* TFS-Arbeitsaufgaben verknüpft, um eine Abhängigkeit (Layer)-Diagramm ist nicht möglich, auf der Entwurfsoberfläche
* Back Verknüpfen von DSL oder einer Ebene wird nicht mehr unterstützt. 
* UML-Erweiterungen in der Modellierungs-SDK wird nicht mehr unterstützt.

Unterstützung für die Architektur von .NET- und C++-Code zu visualisieren erhältlich ist jedoch [codezuordnungen](map-dependencies-across-your-solutions.md), und zu den erheblichen Verbesserungen zum oben beschriebenen abhängigkeitsüberprüfung.

Wenn Sie die UML-Designer eine erhebliche Benutzer sind, können Sie weiterhin Visual Studio 2015 oder früher verwenden, während Sie möchten eine alternative Tool für Ihre Anforderungen UML.

Weitere Informationen finden Sie unter [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/). 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Versionsunterstützung für Architektur- und Modellierungstools  

Visual Studio ist in mehreren Versionen verfügbar. Nicht jede Version bietet Unterstützung für die Architektur- und Modellierungstools. Die folgende Tabelle zeigt die Verfügbarkeit jedes Tools.  
  
|**Funktion**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Codezuordnungen**|Ja|Siehe Hinweis (1)|-|-|  
|**Abhängigkeit von Diagrammen**|Ja|Siehe Hinweis (2)|Siehe Hinweis (2)|-|  
|**Gerichtete Diagramme** (DGML-Diagramme)|Ja|Ja|Ja|-|  
|**Codeklon**|Ja|-|-|-|  
  
Hinweis (1): Unterstützt nur das Lesen und Filtern von Code Maps, das Hinzufügen neuer allgemeiner Knoten und das Erstellen eines neuen gerichteten Diagramms aus einer Auswahl.

Hinweis (2): Unterstützt nur das Lesen der Abhängigkeit Diagramme.
