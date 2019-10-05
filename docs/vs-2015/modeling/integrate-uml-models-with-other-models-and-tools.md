---
title: Integrieren von UML-Modellen in andere Modelle und Tools | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1a8b67e5c784e24b1af71089d33e7db60cb1f92c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68190388"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrieren von UML-Modellen in andere Modelle und Tools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML-Modelle können in andere Modelle und domänenspezifische Sprachen integriert sein.  
  
 Sie können die Modelle wie folgt integrieren, indem Sie Erweiterungscode für eine Vielzahl von Funktionen schreiben:  
  
 Anfügen von Verweisen von einem beliebigen Element an andere Elemente, z. B. an Dateien oder Elemente in anderen Modellen.  
 In einem UML-Element können Sie Links zu anderen UML-Elementen, Dateien oder anderen Objekten speichern, indem Sie deren Identitäten als Zeichenfolgen codieren.  
  
 Sie können z. B. eine Erweiterung schreiben, mit der eine beliebige UML-Aktion (das heißt, ein Element in einem Aktivitätsdiagramm) mit einem anderen Aktivitätsdiagramm verknüpft werden kann. Wenn der Benutzer auf die Aktion doppelklickt, wird das andere Diagramm geöffnet. So kann der Benutzer eine ausführlichere Ansicht der Aktion bereitstellen.  
  
 Zwei Möglichkeiten sind verfügbar, um Zeichenfolgen und andere Daten in einem beliebigen Element zu speichern:  
  
- **Stereotyp-Eigenschaften.** Sie können ein UML-Profil definieren, in dem Sie ein Stereotyp definieren, das Eigenschaften zu bestimmten Arten von UML-Elementen hinzufügt. Sie können beispielsweise ein Profil, das eine Eigenschaft namens fügt definieren **MoreDetail** , einer UML-Aktion. Sie können Erweiterungscode schreiben, mit dem Linkdaten in einer Aktion gespeichert werden, indem das Stereotyp auf die Aktion angewendet wird und anschließend die Daten in der Eigenschaft gespeichert werden.  
  
   Das Stereotyp und dessen Eigenschaften sind für Benutzer im Eigenschaftenfenster sichtbar.  
  
   Zum Bereitstellen dieser Erweiterung packen Sie die Profildefinition und den Erweiterungscode in einer einzelnen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Erweiterung.  
  
   Weitere Informationen finden Sie unter [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md).  
  
   Ein Beispielprojekt, in dem ein Profil mit Menübefehlen und gestenhandlern bereitgestellt wird, finden Sie unter [Beispiel: UML-Profile](http://go.microsoft.com/fwlink/?LinkID=213811).  
  
- **Verweise.** An jedes UML-Element können Sie einen Satz von Zeichenfolgen anfügen. Sie können Code schreiben, in dem die Informationen gespeichert werden, z. B. ein Dateiname oder die GUID eines anderen Elements. Dazu müssen Sie keine weiteren Definitionen bereitstellen. Verweise sind für Benutzer nicht direkt sichtbar.  
  
   Weitere Informationen finden Sie unter [Anfügen von Referenzzeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md). Ein Beispiel finden Sie unter [Verknüpfen von UML-Elementen mit Diagrammen oder anderen Dateien](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
  Es gibt zwei Möglichkeiten, Verweise auf Modellelemente zu codieren:  
  
- **GUID und den Dateinamen** dem Zielmodellelement und das Modell, das es enthält oder einem bestimmten Diagramm, das es anzeigt.  
  
   Ein Beispiel finden Sie unter [Verknüpfen von UML-Elementen mit Diagrammen oder anderen Dateien](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
- **ModelBus-Verweise.** ModelBus ist ein Framework zum Erstellen und Auflösen von Verweisen zwischen Modellen. Enthalten ist die ModelBus-Auswahl, mit der Benutzer ein Element in einem Modell auswählen können. Zudem können Verweise leichter aufgelöst werden, die aufgrund von Änderungen im Zielmodell verloren gehen.  
  
   Weitere Informationen finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
  Weitergeben von Änderungen von einem Modell an ein anderes.  
  Sie können z. B. den Namen eines Elements mit dem Namen des verknüpften Diagramms synchronisieren, damit bei Änderungen des einen der andere ebenfalls geändert wird. Dafür sind zwei Mechanismen verfügbar:  
  
1. **VMSDK-Regeln** kann verwendet werden, um Änderungen innerhalb desselben Modells weiterzugeben.  
  
    Ein Beispiel finden Sie unter [Verknüpfen von UML-Elementen mit Diagrammen oder anderen Dateien](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
2. **VMSDK-Ereignisse** kann verwendet werden, Änderungen außerhalb des Modells – z. B. weitergegeben werden, so ändern Sie den Dateinamen eines verknüpften Dokuments oder ein Element in einem anderen Modell zu ändern.  
  
   Weitere Informationen zu beiden Mechanismen finden Sie unter [Vorgehensweise: Reagieren auf Änderungen in einem UML-Modell](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
   Modellübergreifendes Kopieren von Elementen durch Ziehen  
   Sie können es ermöglichen, dass Benutzer Elemente erstellen, indem sie Elemente in ein UML-Diagramm ziehen. Das erstellte Element muss keine Kopie des Originals sein. Sie können es den Benutzern beispielsweise ermöglichen, ein Aktivitätsdiagramm aus dem Projektmappen-Explorer in ein anderes Aktivitätsdiagramm zu ziehen, um eine neue Aktion zu erstellen.  
  
   Weitere Informationen finden Sie unter [Definieren eines gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) und [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="samples"></a>Proben  
 Informieren Sie sich das Codebeispiel [Verknüpfen von UML-Elementen mit Diagrammen oder anderen Dateien](http://go.microsoft.com/fwlink/?LinkId=213813). Anhand des Beispiels können Benutzer eine Datei auf ein beliebiges UML-Element ziehen und die Datei später durch Doppelklicken auf das Element öffnen. Sie können z. B. ein Aktivitätsdiagramm mit einem Anwendungsfallelement verknüpfen. Ein Symbol gibt an, welche Elemente über Links verfügen.  
  
 Diese Verfahren werden im folgenden Codebeispiel veranschaulicht:  
  
- [Anfügen von Referenzzeichenfolgen an UML-Modellelemente](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
   Im Beispielcode werden Dateipfade und Element-GUIDs in dem Element zugeordneten Verweiszeichenfolgen gespeichert.  
  
- Hinzufügen von Decorator-Elementen zu UML-Elementen. Allgemeine Informationen zu Decorator-Elemente, finden Sie unter [Anpassen von Text- und Image-Feldern](../modeling/customizing-text-and-image-fields.md).  
  
   Im Beispiel wird den UML-Formen ein Decorator-Bildelement hinzugefügt.  
  
- [Vorgehensweise: Reagieren Sie auf Änderungen in einem UML-Modell](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
   Das Beispiel veranschaulicht das Definieren einer Regel, die auf neu in einem Diagramm angezeigte Formen reagiert.  
  
- [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Definieren eines Gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
   Das Beispiel zeigt, wie die Elemente behandelt werden, die von Windows-Explorer (oder von Datei-Explorer), dem Projektmappen-Explorer und anderen UML-Elementen gezogen werden.  
  
  Ein Beispiel, in dem ein UML-Modell ist, von einem DSL gelesen werden, finden Sie unter [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines Menübefehls in einem Modellierungsdiagramm](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definieren eines gestenhandlers in einem Modellierungsdiagramm](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Vorgehensweise: Hinzufügen eines Drag & Drop-Handlers](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Vorgehensweise: Reagieren Sie auf Änderungen in einem UML-Modell](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [Beispiel: UML-Profile](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [Verknüpfen von UML-Elementen mit Diagrammen oder anderen Dateien](http://go.microsoft.com/fwlink/?LinkId=213813)
