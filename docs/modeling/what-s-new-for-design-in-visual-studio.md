---
title: Neues beim Entwurf in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 32
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
ms.sourcegitcommit: 17bc5792d4fa9fac0b97705e61372dcc884c82a2
ms.openlocfilehash: 2704914ab8607e0a7442a45589e6a6cab08b7338
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-for-design-in-visual-studio"></a>Neues beim Entwurf in Visual Studio

## <a name="live-dependency-validation"></a>Live abhängigkeitsüberprüfung

Entfernen unerwünschte Abhängigkeiten ist ein wichtiger Bestandteil der Verwaltung Ihrer technischen Schulden.
Live-Überprüfung der Abhängigkeiten ist jetzt enthalten, genaue Informationen zu Problemen mit der Bereitstellung und vollständig gelten die neuen Funktionen in der Fehlerliste und Editor.

![Live abhängigkeitsüberprüfung in Aktion](~/docs/modeling/media/dep-validation-whatsnew-01.png)

Die Möglichkeiten für die Erstellung wurde geändert, um abhängigkeitsüberprüfung, übersichtlicher und besser zugänglich sind, ändern die Terminologie von "Ebenendiagramm", "Abhängigkeitsdiagramm".

Die **Architektur** Menü enthält jetzt den Befehl direkt einem Abhängigkeitsdiagramm erstellen:

![Live-Abhängigkeit Element Menü Architektur](~/docs/modeling/media/dep-validation-whatsnew-02.png)

... und den Namen einer Ebene in einem Abhängigkeitsdiagramm und deren Beschreibung wurden geändert, um aussagekräftigere:

![Live-Abhängigkeit Eigenschaftennamen aktualisiert](~/docs/modeling/media/dep-validation-whatsnew-03.png)

Hier sehen Sie die Auswirkung der Änderungen sofort in die Ergebnisse der Analyse für den aktuellen Code in der Lösung jedes Mal, wenn Sie das Diagramm speichern. Sie müssen nicht mehr warten, bis die Ausführung des Befehls "Abhängigkeiten überprüfen".

Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/). 
 
## <a name="uml-designers-have-been-removed"></a>UML-Designern wurden entfernt

Die UML-Designern wurden von der Visual Studio Enterprise-Version entfernt.

* UML-Diagramme sind jetzt als XML-Dateien angezeigt.
* UML-Modell-Explorer ist nicht mehr vorhanden.
* Modellierungsprojekt Verweise für die Validierung der Abhängigkeit nicht mehr verwendet werden
* Der Knoten "Layer Verweise" im Projektmappen-Explorer wird nicht mehr angezeigt.
* Der Buildvorgang "Validate" in einem Abhängigkeitsdiagramm (Layer) wird nicht mehr verwendet – die Build-Aufgabe wurde entfernt 
* Die Struktur des Projekts wird für Roundtrips zwischen den Versionen beibehalten.
* Sie können weiterhin öffnen, erstellen, bearbeiten, und speichern ein Abhängigkeitsdiagramm (Layer) als XML
* TFS-Arbeitsaufgaben verknüpft, um ein Abhängigkeitsdiagramm (Layer) werden nicht auf der Entwurfsoberfläche zugegriffen.
* Wieder Verknüpfen von DSL oder einer Ebene wird nicht mehr unterstützt. 
* UML-Erweiterbarkeit in die Modeling SDK wird nicht mehr unterstützt.

Unterstützung für die Architektur von .NET und C++-Code zu visualisieren erhältlich ist jedoch [codezuordnungen](map-dependencies-across-your-solutions.md), und die oben beschriebenen abhängigkeitsüberprüfung deutlich verbessert.

Wenn Sie eine erhebliche der UML-Designer verwenden, können Sie weiterhin Visual Studio 2015 oder frühere Versionen verwenden, während Sie möchten eine alternative Tool für Ihre Bedürfnisse UML.

Weitere Informationen finden Sie unter [in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/). 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Versionsunterstützung für Architektur- und Modellierungstools  

Visual Studio ist in mehreren Versionen verfügbar. Nicht jede Version bietet Unterstützung für die Architektur- und Modellierungstools. Die folgende Tabelle zeigt die Verfügbarkeit jedes Tools.  
  
|**Funktion**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Codezuordnungen**|Ja|Siehe Hinweis (1)|-|-|  
|**Abhängigkeitsdiagramme**|Ja|Siehe Hinweis (2)|Siehe Hinweis (2)|-|  
|**Gerichtete Diagramme** (DGML-Diagramme)|Ja|Ja|Ja|-|  
|**Code-Klon**|Ja|-|-|-|  
  
Hinweis (1): Unterstützt nur das Lesen und Filtern von Code Maps, das Hinzufügen neuer allgemeiner Knoten und das Erstellen eines neuen gerichteten Diagramms aus einer Auswahl.

Hinweis (2): Unterstützt nur das Lesen von Abhängigkeitsdiagramme.

